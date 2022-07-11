# Sniffing

Depending on the network topology, there are many ways of gaining read-access to a network to conduct passive attacks. The most common method compromises a general purpose operating system on the segment and installs sniffer software that puts a network interface card in promiscuous mode and captures traffic. [ARP/MAC spoofing](ARP-spoofing.md) may be necessary to sniff traffic on switched networks.

## Attack tree

```text
1 Get into a good spot (AND)
    1.1 Gain local network access to a segment (OR)
        1.1.1 Compromise server (AND)
        1.1.2 Install and use sniffing software
    1.2 Tap physical medium (OR)
    1.3 Redirect traffic through a compromised host    
2 Sniff information 
    2.1 Email traffic
    2.2 FTP passwords
    2.3 Web traffic
    2.3 Telnet passwords
    2.4 Router configuration
    2.5 Chat sessions
    2.6 DNS traffic
```

## Scripts

* [simple sniffer script](https://github.com/tymyrddin/ymrir/tree/master/packet_sniffer)

## Network tools
* [BetterCAP](https://www.bettercap.org/)
* [EtterCAP](https://www.ettercap-project.org/)
* [Wireshark](https://www.wireshark.org/)
* [Tcpdump](https://www.tcpdump.or/)
* [WinDump](https://www.winpcap.org/windump/)
* [OmniPeek](https://store.liveaction.com/product/omnipeek-network-protocol-analyzer/)
* [Dsniff](https://www.monkey.org/~dugsong/dsniff/)
* [EtherApe](https://etherape.sourceforge.io/) available as package





