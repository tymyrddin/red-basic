# ARP spoofing

## Attack tree

```text
1 Use an ARP spoofing tool such as Arpspoof, Cain & Abel, Arpoison, or Ettercap
    1.1 Set the IP address of the tool to match the IP subnet of the victim (scans the network to find out 
        the IP address and MAC address of all the hosts on the subnetwork) (AND)
    1.2.Select a target (AND)
    1.3 Send ARP packet, replacing the MAC address of the target with own MAC address while keeping IP address 
        as is, causing packets meant for the target now being rerouted to the attacker (AND)
    1.4 When packets for the victim arrive, launch further attacks
        1.4.1 Associate multiple IP addresses to a single MAC address on a network (IP aliasing)
        1.4.2 Sit in between the communication between two users (MitM)
        1.4.3 Hijack session (network)
        1.4.4 Perform a DoS
```

## Notes

There are two different addressing schemes for computers on a LAN, the global IP address and the local MAC address. The Address Resolution Protocol (ARP) was created to carry IP traffic. By merely injecting two ARP Reply packets into a trusting LAN, any device is able to receive all traffic going back and forth between any two devices on the LAN. 

In an ARP spoofing attack, an adversary sends spoofed ARP messages over a LAN in order to link the adversary's MAC address with the IP address of a legitimate member of the network. Data that is intended for the host’s IP address gets sent to the adversary instead.
* ARP spoofing can be used to steal information, modify data-in-transit or stop traffic on a LAN.
* ARP spoofing attacks can also be used to facilitate other types of attacks, including [DoS](DoS.md) attacks, [session hijacking](Hijack-network-session.md) and [MitM](MitM.md) attacks.

## Demo scripts
* [simple ARP spoofer script](https://github.com/tymyrddin/ymrir/tree/master/arp_spoofer)
* [simple file interceptor](https://github.com/tymyrddin/ymrir/tree/master/file_interceptor)
* [simple code injecor](https://github.com/tymyrddin/ymrir/tree/master/code_injector)

## Network tools
* [dsniff](https://www.monkey.org/~dugsong/dsniff/)
* [arpwatch](https://ee.lbl.gov/)


