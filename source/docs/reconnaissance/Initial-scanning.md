# Initial scanning

Research network architecture, defence mechanisms, operating systems and applications. Find where the company resources are logically located. Once the IP addresses are known, probe and scan the network for vulnerable hosts, applications, or infrastructure equipment.

* Use a ping sweep to find what hosts are currently live on the network.
* Probe by looking for open ports on the available host computers to discover services.
* Most common applications use well-defined port numbers. Use the open port information further to discover the OS and the application servicing the port.
* Know, learn or research the vulnerabilities of OSs and the applications they run.
* Make a map of the hosts, servers, and weaknesses to exploit in the future. Keep adding to the map as more is discovered later in the process.

## Examples

```
# nmap -sn -T4 -oG Discovery.gnmap 192.168.9.1/24  
Starting Nmap 7.91 ( https://nmap.org ) at 2021-03-13 18:47 UTC
Nmap scan report for LEDE.lan (192.168.9.1)
Host is up (0.00022s latency).
MAC Address: C1:4F:B2:BD:1A:3E (Tp-link Technologies)
Nmap scan report for machine.lan (192.168.9.173)
Host is up (0.00025s latency).
MAC Address: B3:BC:70:43:33:05 (Pegatron)
Nmap scan report for kali.lan (192.168.1.89)
Host is up.
Nmap done: 256 IP addresses (3 hosts up) scanned in 2.04 seconds
```

Enumerating live hosts in a file 

```
# grep "Status: Up" Discovery.gnmap | cut -f 2 -d ' ' > LiveHosts.txt  
```
                                                                                 
Scanning TCP ports:

```
# nmap -sS -T4 -Pn -oG TopTCP -iL LiveHosts.txt
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-03-13 18:53 UTC
Nmap scan report for LEDE.lan (192.168.9.1)
Host is up (0.00042s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
443/tcp  open  https
5000/tcp open  upnp
MAC Address: C1:4F:B2:BD:1A:3E (Tp-link Technologies)

Nmap scan report for machine.lan (192.168.1.173)
Host is up (0.00014s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
MAC Address: B3:BC:70:43:33:05 (Pegatron)

Nmap scan report for kali.lan (192.168.1.89)
Host is up (0.000024s latency).
All 1000 scanned ports on kali.lan (192.168.1.89) are closed

Nmap done: 3 IP addresses (3 hosts up) scanned in 38.54 seconds
```
    
Scanning UDP ports:                                                                         

```
# nmap -sU -T4 -Pn -oN TopUDP -iL LiveHosts.txt

Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-03-13 18:54 UTC
Warning: 192.168.1.1 giving up on port because retransmission cap hit (6).
Warning: 192.168.1.173 giving up on port because retransmission cap hit (6).

# nmap -sU -T3 -Pn -oN TopUDP -iL LiveHosts.txt                      

Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-03-13 19:02 UTC
Nmap scan report for LEDE.lan (192.168.1.1)
Host is up (0.00047s latency).
Not shown: 995 closed ports
PORT     STATE         SERVICE
53/udp   open          domain
67/udp   open|filtered dhcps
123/udp  open|filtered ntp
1900/udp open|filtered upnp
5351/udp open          nat-pmp
MAC Address: C1:4F:B2:BD:1A:3E (Tp-link Technologies)

Nmap scan report for machine.lan (192.168.1.173)
Host is up (0.00046s latency).
Not shown: 997 closed ports
PORT     STATE         SERVICE
623/udp  open          asf-rmcp
631/udp  open|filtered ipp
5353/udp open|filtered zeroconf
MAC Address: B3:BC:70:43:33:05 (Pegatron)

Nmap scan report for kali.lan (192.168.1.89)
Host is up (0.000021s latency).
All 1000 scanned ports on kali.lan (192.168.1.89) are closed

Nmap done: 3 IP addresses (3 hosts up) scanned in 1086.87 seconds
```

Full scan:                                                                            

```
# nmap -sS -T4 -Pn -p 0-65535 -oN FullTCP -iL LiveHosts.txt
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-03-13 19:23 UTC
Nmap scan report for LEDE.lan (192.168.1.1)
Host is up (0.00044s latency).
Not shown: 65531 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
443/tcp  open  https
5000/tcp open  upnp
MAC Address: C1:4F:B2:BD:1A:3E (Tp-link Technologies)

Nmap scan report for machine.lan (192.168.1.173)
Host is up (0.00039s latency).
Not shown: 65534 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
MAC Address: B3:BC:70:43:33:05 (Pegatron)

Nmap scan report for kali.lan (192.168.1.89)
Host is up (0.0000090s latency).
All 65536 scanned ports on kali.lan (192.168.1.89) are closed

Nmap done: 3 IP addresses (3 hosts up) scanned in 2621.10 seconds
```

Detect services:

```
# nmap -sV -T4 -Pn -oG ServiceDetect -iL LiveHosts.txt               
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-03-13 21:34 UTC
Nmap scan report for LEDE.lan (192.168.1.1)
Host is up (0.00044s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE  VERSION
22/tcp   open  ssh      Dropbear sshd (protocol 2.0)
53/tcp   open  domain   dnsmasq 2.81
80/tcp   open  http     LuCI Lua http config
443/tcp  open  ssl/http LuCI Lua http config
5000/tcp open  upnp     MiniUPnP 2.0 (OpenWrt; UPnP 1.1)
MAC Address: C1:4F:B2:BD:1A:3E (Tp-link Technologies)
Service Info: OS: Linux; Device: broadband router; CPE: cpe:/o:linux:linux_kernel

Nmap scan report for machine.lan (192.168.1.173)
Host is up (0.00040s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
80/tcp open  http    Apache httpd 2.4.38 ((Debian))
MAC Address: B3:BC:70:43:33:05 (Pegatron)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Nmap scan report for kali.lan (192.168.1.89)
Host is up (0.000016s latency).
All 1000 scanned ports on kali.lan (192.168.1.89) are closed

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 3 IP addresses (3 hosts up) scanned in 71.69 seconds
```

OS detection:

```                                                           
# nmap -O -T4 -Pn -oG OSDetect -iL LiveHosts.txt        
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-03-13 21:43 UTC
Nmap scan report for LEDE.lan (192.168.1.1)
Host is up (0.00045s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
443/tcp  open  https
5000/tcp open  upnp
MAC Address: C1:4F:B2:BD:1A:3E (Tp-link Technologies)
Device type: WAP
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3.18 cpe:/o:linux:linux_kernel:4.1
OS details: OpenWrt Chaos Calmer 15.05 (Linux 3.18) or Designated Driver (Linux 4.1 or 4.4)
Network Distance: 1 hop

Nmap scan report for machine.lan (192.168.1.173)
Host is up (0.00039s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
MAC Address: B3:BC:70:43:33:05 (Pegatron)
Device type: general purpose
Running: Linux 4.X|5.X
OS CPE: cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel:5
OS details: Linux 4.15 - 5.6
Network Distance: 1 hop

Nmap scan report for kali.lan (192.168.1.89)
Host is up (0.000090s latency).
All 1000 scanned ports on kali.lan (192.168.1.89) are closed
Too many fingerprints match this host to give specific OS details
Network Distance: 0 hops

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 3 IP addresses (3 hosts up) scanned in 41.76 seconds
```

## Cheatsheets

* [Nmap cheatsheet](https://github.com/tymyrddin/nest-egg/blob/main/cheatsheets/Nmap-cheatsheet.md)
* [Ports cheatsheet](https://github.com/tymyrddin/nest-egg/blob/main/cheatsheets/Ports-cheatsheet.md)
