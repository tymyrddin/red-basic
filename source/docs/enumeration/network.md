# Network enumeration

## Attack tree

```text
1 Enumerate
    1.1 Hosts on the network (AND)
    1.2 Network and create a network topology (for example with Zenmap) (AND)
    1.3 Domains (Whois lookups and DNS profiling)
```

## Notes

* Zenmap does a deep scan, which will identify the hosts and services on the network, and help create a network topology
* Enumerating Domains can be done with [DNS profiling](../reconnaissance/dns.md).

## Tools

* [Nmap](https://www.kali.org/tools/nmap/)
* [Zenmap](https://www.kali.org/tools/zenmap-kbx/)

