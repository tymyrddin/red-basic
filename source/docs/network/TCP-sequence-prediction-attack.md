# TCP sequence prediction attack

TCP suffers from well-known design flaws which make it possible to hijack or terminate applications that use it as their transport protocol. A SCP sequence prediction attack is an attempt to predict the sequence number used to identify the packets in a TCP connection, which can be used to forge packets, for example in a BGP Hijack.

## Attack

```
1 Blind spoofing attack (OR)
    1.1 Guess sequence number use (AND)
    1.2 Inject valid message 
2 Non-blind spoofing attack
    2.1 Sniff traffic (AND)
    2.2 Inject valid message based on sequence numbers
```