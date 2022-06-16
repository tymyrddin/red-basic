# Ping sweep

## Attack tree

```text
1 Send out ICMP echo requests to every system on a particular network or subset of a 
network to determine which hosts are up.
```

## Notes


* If a service is listening on a port and someone makes a connection to it (by sending a SYN packet), the service will send a SYN/ACK packet in return. That means that there is a machine at that IP address.
* If no service is listening on that port but the machine is up and running and on the network, a reset (RST) packet will be sent back. That means there is nothing listening on that port, but having sent something in return means that a machine is at that IP address.
* If nothing is received after sending a SYN packet, it means there is no host at that IP address OR a firewall is blocking traffic OR the host is down. Port 80 is therefore extremely useful for ping sweeps, because most firewalls and port filters do not block web traffic.

|Send |Receive  |Send |Assumption  |
| --- | --- | --- | --- | 
|`SYN`|`SYN/ACK`|`ACK` followed by `RST`|Port is open, host is up|
|`SYN`|`RST`|-|Port is closed, host is up|
|`SYN`|Nothing|-|Port is blocked by firewall, host is down, or there is no host at that IP address|

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

# grep “Status: Up” Discovery.gnmap | cut -f 2 -d ' ' > LiveHosts.txt
```

## Cheatsheets

* [Nmap cheatsheet](https://github.com/tymyrddin/nest-egg/blob/main/cheatsheets/Nmap-cheatsheet.md)
