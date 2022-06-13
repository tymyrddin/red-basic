# Man-in-the-Middle (MitM)

A Man-in-the-Middle (MitM) attack is a general term for when an adversary positions herself in the middle of a conversation (usually between a user and an application on the application or cryptograhic layer). A MitM attack allow an adversary to proxy communication between two parties allowing any data to either be read or altered. For example to eavesdrop or to steal personal information such as login credentials, account details, tokens and credit card numbers. This information can then further be used for unapproved fund transfers, password changes, impersonation, complete identity theft and for gaining a foothold during the infiltration stage of a structured hack.

* The adversary first subverts the address infrastructure (intercepts traffic). In passive interception forms, an adversary makes, for example, an infected WiFi hotspot available to the public. Active forms use some sort of spoofing. 
* After subverting the address infrastructure, any two-way encrypted traffic needs to be decrypted. This can be done by, for example, SSL spoofing (does not attack SSL itself, but the transition from non-encrypted to encrypted communications), spoofing HTTPS, an SSL BEAST attack, or hijacking SSL
* [Session replay](Replay-attack.md) and hijacking attacks can be used to bypass authentication.
* If a root certificate can be installed on the target, the adversary can replace it and maintain a secure connection.
* When BGP session hijacking, DNS spoofing is likely not very useful because of hostnames not being used in router configurations.

## Attack

```
1 Subvert address infrastructure (AND)
    1.1 L2 Spoofing 
        1.1.1 ARP/MAC spoofing (OR)
        1.1.2 VLAN hopping (OR)
        1.1.3 STP (RSTP, PVSTP, MSTP) spoofing (OR)
    1.2 L3 Spoofing 
        1.2.1 SLAAC attack (OR)
        1.2.2 Hijacking HSRP (VRRP, CARP) (OR)
        1.2.3 Hijacking BGP (OR)
        1.2.4 Routing table poisoning (OR)
        1.2.5 Redirecting ICMP (OR)
    1.3 L4+ Spoofing
        1.3.1 NetBIOS (LLMNR) spoofing (OR)
        1.3.2 DHCP spoofing (OR)
        1.3.3 Rogue Access Point (OR)
        1.3.4 IP spoofing (OR)
        1.3.5 DNS spoofing (OR)
2 Decrypt (AND)
    2.2 SSL BEAST (OR)
    2.3 Hijack SSL (OR)
    2.4 Strip SSL
3 Do whatever 
```

## Resources

* [simple ARP spoofer](https://github.com/tymyrddin/ymrir/tree/master/arp_spoofer)
* [simple DNS spoofer](https://github.com/tymyrddin/ymrir/tree/master/dns_spoofer)

## Notes

* NetBIOS is outdated but still lives on in some older systems, sometimes for backward compatability. It is the equivalent of broadcasting names to look for each other but is not routable. It is local network only. If no one on the other network can use it for your network, then no one there can access your NetBIOS shared folders and printers, unless one has gained access to your local network. You can also access NetBIOS machines with a WINS server. That is the NetBIOS equivalent of a DNS server. 
