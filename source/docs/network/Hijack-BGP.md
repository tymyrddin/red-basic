# Hijack BGP

BGP hijacking happens often, there's no practical way to prevent it, we have to live with it. Internet routing was designed to be a conversation between trusted parties. HTTPS encryption is backed by SSL/TLS PKI, which itself trusts Internet routing. Routing announcements are accepted practically without any validation, creating the possibility of a network operator announcing someone else's network prefixes without permission. Testing has shown that sending spoofed updates as a blind adversary is more difficult than thought, while launching this attack from a compromised/misconfigured router turned out relatively easy.

A BGP hijack can be used to disable critical portions of the Internet by disrupting Internet routing tables, force a multi-homed AS to use an alternate path to/from an outside network instead of the preferred path, disable single-homed and multi-homed AS, to blackhole traffic and in MitM attacks.

## Attack

```
1 Send from valid router (OR)
    1.1 Misconfigured (OR)
    1.2 Compromise router
2 Send from invalid router
    2.1 Gag valid router (AND)
        2.1.1 Kill router
            2.1.1.1 Power Off/Physical Layer (OR)
            2.1.1.2 Crash and prevent reboot (OR)
            2.1.1.3 Conduct denial of service against router 
        2.1.2 Steal IP Address
            2.1.2.1 ARP Spoof (OR)
            2.1.2.2 Steal MAC
    2.2 Introduce rogue router (Assume IP)
    2.2.1 Steal IP Addr
    2.2.2. More Specific Route Introduction
    2.2.3. Establish unauthorized BGP session with peer
3 Send spoofed BGP Update from Non-Router
    3.1 Conduct TCP Sequence Number Attack
    3.2 Conduct Man-in-the-Middle
4 Craft BGP Message 
```