# Distributed Denial of Service (DDoS)

A DoS is distributed from only one starting point, whereas a DDoS implies several computers or servers. Amplification is dependent on the amount of zombies in the botnet used. In UDP spoofing the IP address of the packet (where it comes from) is replaced by the IP address of the target. The answers to the sent packets will thus come back to the target, and not to the attacker. Amplification is dependent on the number of zombies in the botnet and the used protocol (attack vector). Everything that works on UDP presents a good amplification factor and allows spoofing are prime candidates, such as game servers, time servers (NTP) or Domain Name Servers.

## Attack

```
1 UDP (User Datagram Protocol) spoofing
2 Create zombies
    2.1 Voluntary “botnet”
    2.2 Create a botnet
3 Launch DoS vector
    3.1 UDP Flood (OR)
    3.2 TCP SYN Flood (OR)
    3.3 ICMP echo request Flood (OR)
    3.4 ICMP directed broadcast (like smurf)
    3.5 NTP Flood
    3.6 Another UDP based protocol whose answers are longer than the questions
```