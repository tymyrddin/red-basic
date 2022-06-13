# Denial of Service (DoS)

The two most devastating variations of Denial of Service attacks are the [distributed denial of service (DDoS)](DDoS.md) and the [distributed deflection denial of service (DrDoS)](DrDoS.md). Both types enlist the assistance of others, voluntary or not, to assist in the attack. This significantly increases the size of the attack, shields the source, and makes defending from it harder.

## Attack

```
1 Physical destruction of router (OR)
2 Link layer attacks (OR)
    2.1 Protocol attack using link layer protocol (OR)
    2.2 Physical link attack
3 ARP attacks (OR)
4 IP attacks (OR)
    4.1 ICMP Message (OR)
        4.1.1 Ping O' Death: Send one or more oversized ping packets (larger than 65,536 bytes) (OR)
        4.1.2 Malformed
    4.2 IP Fragmentation Attack
5 UDP attacks (OR)
6 TCP attacks (OR)
    6.1 TCP SYN Flood: Trick target into thinking a session is being established by creating half-open connections (OR)
    6.2 Connect() (OR)
    6.3 LAST_ACK (OR)
    6.4 New/undiscovered DoS against TCP
7 Application-Layer DoS (OR)
    7.1 Telnet (OR)
    7.2 SSH (OR)
    7.3 SNMP (OR)
    7.4 HTTP (OR)
        7.4.1 HTTP Flood (OR)
        7.4.2 Long form field submission through POST method (OR)
        7.4.3 Partial requests (OR)
        7.4.4 Junk HTTP GET and POST requests
    7.5 Other application layer protocol
```

## Notes



