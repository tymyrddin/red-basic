# Hijack session (network)

Often two types of session hijacking are distinguished depending on how they are done. If the attacker directly gets involved with the target, it is called active hijacking, and if an attacker just passively monitors the traffic, it is called passive hijacking (but is really just sniffing).

## Attack

```
    1 Active
        1.1 Silence the (usually client) device with a DoS (AND)
        1.2 Take over the devices' position in the communication exchange between device and server (AND)
            1.2.1 Use TCP sequence prediction attack
        1.3 Create new user accounts on the network to gain access to the network later
    2 Passive
        2.1 Monitor the traffic between client and server
        2.2 Discover valuable information or passwords
```