# Distributed Deflection Denial of Service (DrDoS)

## Attack tree

```text
1 IP spoofing of machines and servers (AND)
2 Attack
    2.1 Call a large number of servers (DNS, NTP, Game servers) using a legitimate UDP request (amplification coefficient of between 20 and 50) (OR)
    2.2 Call a large number of servers using a TCP SYN request (amplification coefficient of 10)
```

## Notes

In a DrDoS attack, the requests meant for a target are sent using systems earlier compromised.