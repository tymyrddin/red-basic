# Side-channel attack

## Attack tree

```text
1 Monitor the emissions produced by electronic circuits when the target's computer 
    is being used to exploit information about power consumption and electromagnetic fields for 
    reverse engineering (side-channel attack) (OR)
2 Use the sounds a central processing unit (CPU) produces (acoustic attack) (OR)
3 Exploits how and when cache is accessed (cache attack) (OR)
4 Use information by introducing faults into the system’s computations (differential fault analysis attack) (OR)
3 Monitor the movement of data to and from a system's CPU and memory (timing attack, 
    for example AES side-channel attack) (OR)
4 Use infrared images to monitor the surface of a CPU chip (thermal-imaging attack) (OR)
5 Collect information about hard disk activity by using a audio/visual recorder (optical side-channel attack) (OR)
6 Monitor the electromagnetic fields produced by data as it moves through the computer (Van Eck phreaking)
```

## Notes

A side-channel attack (SCA) is a security exploit that involves collecting information about what a computing device does when it is performing cryptographic operations.

## Mitigation

### Development
* Randomise the order of operations on data within the system to make it more difficult for an adversary.
* Increase the amount of noise in a channel.

### Individuals
* Faraday cages can also be used to reduce electromagnetic leaks. This is akin to wearing aluminium hats.


