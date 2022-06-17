# DNS spoofing

## Attack tree

```text
1 Hijack a local DNS (OR)
    1.1 Install malware on host
    1.2 Change local DNS settings for a redirect
2 Poison DNS cache (OR)
    2.1 Install a dns spoofing tool such as dns-spoof or ManOnTheSideAttack-DNS Spoofing (AND)
    2.2 Sniff the network traffic and intercept all DNS queries matching a given domain name from the victim (AND)
    2.3 Forge and send a valid response (the corrupt data gets cached by the DNS name server) (AND)
        2.3.1 Redirect the target domain's name server (cache an additional A-record for ns.target.example) (OR)

        +---------------------+
        | ANSWER              | (no response)
        +---------------------+
        | AUTHORITY           | adversary.example. 3600 IN NS ns.target.example.
        +---------------------+
        | ADDITIONAL          | ns.target.example. IN A xxx.xxx.xxx.xxx
        +---------------------+

        2.3.2 Redirect the NS record to another target domain (cache unrelated authority information for target.example's NS-record)

        +---------------------+
        | ANSWER              | (no response)
        +---------------------+
        | AUTHORITY           | target.example. 3600 IN NS ns.adversary.example.
        +---------------------+
        | ADDITIONAL          | ns.adversary.example. IN A xxx.xxx.xxx.xxx
        +---------------------+

    2.4 When the cache is poisoned (if it is a major DNS server, it can poison the caches of DNS servers 
    maintained by internet service providers), launch further attacks
3 Hijack a Router DNS (OR)
    3.1 Compromise router (AND) 
        3.1.1 Default passwords (OR)
        3.1.2 Use firmware vulnerabilities
    3.2 Overwrite DNS settings
4 Rogue DNS Server (OR)
    4.1 Compromise a DNS server (AND) 
    4.2 Change DNS records to redirect DNS requests
5 Use DNSSEC vulnerabilities
    5.1 Lack of data confidentiality (Sniff and use for further attacks)
    5.2 Misconfigured DNSSEC
    5.3 Zone enumeration (Only NSEC, NSEC3 and NSEC5 publish hashed records of hostnames)
```

## Notes

DNS spoofing can be achieved by DNS redirection, an attack in which an adversary modifies a DNS server in order to redirect a specific domain name to a different IP address. In many cases, the new IP address will be for a server controlled by the adversary which contains files infected with malware. Cache poisoning is another way to achieve DNS spoofing, without relying on DNS hijacking (physically taking over the DNS settings). An adversary inserts a forged DNS entry, containing an alternative IP destination for the same domain name, after which the DNS server resolves the domain to the spoofed website, until the cache is refreshed.

* DNS server spoofing attacks are often used to spread computer worms and viruses.
* This kind of attack is also often used for pharming.

## Scripting

* [Hijack local DNS](https://github.com/tymyrddin/ymrir/tree/master/dns_spoofer)