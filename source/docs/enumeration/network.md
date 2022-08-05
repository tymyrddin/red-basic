# Network enumeration

## Attack tree

```text
1 Get information
    1.1 LDAP can reveal possible shares, users and other resources on a windows network (AND)
    1.2 SNMP can have default community strings (passwords) set (AND)
    1.3 SMTP can give information like server name, organisational email structure, whether it takes connections (useful for bouncing) (AND)
    1.4 NTP can give time stamps for the network and what it is set to (some protocols are extremely sensitive to time shifts) (AND)
    1.5 DNS may give machine names and/or network services, and may even allow a (partial or whole) zone transfer (AND)
    1.6 Network devices can be many, and some allow for becoming a listener on your behalf (AND)
    1.7 Network traffic can be sniffed to detect what services are running on the network (AND)
```

## Tools

* [Wireshark](https://www.wireshark.org/)
* [DNSrecon](https://github.com/darkoperator/dnsrecon) was written by Carlos Perez in 2006. It was originally written in Ruby, but now has a Python port, which is what is running in Kali. 
* [P0f](https://lcamtuf.coredump.cx/p0f3/)
* [net-snmp](http://www.net-snmp.org/)
* [Onesixtyone](https://www.aldeid.com/wiki/Onesixtyone)

