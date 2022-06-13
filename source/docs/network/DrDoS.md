# Distributed Deflection Denial of Service (DrDoS)

## Attack

```
1 IP spoofing
    1.1 Call a large number of servers (DNS, NTP, Game servers) using a legitimate UDP request (amplification coefficient of between 20 and 50)
    1.2 Call a large number of servers using a TCP SYN request (amplification coefficient of 10)
```