# DNS attacks

## Attack tree

```text
1 DNS poisoning
2 DNS amplification for DDoS attacks on other servers
    2.1 Create a botnet to send thousands of lookup requests to open DNS servers (with a spoofed source address 
    and configured to maximize the amount of data returned by each DNS server)
3 DDoS attack against a DNS server itself 
```

## Notes

* DNS cache poisoning, also known as DNS spoofing, exploits vulnerabilities in the domain name system DNS to divert Internet traffic away from legitimate servers and towards fake ones. This kind of attack is often used for pharming.
* DNS amplification attacks exploit the open nature of DNS services to strengthen the force of distributed denial of service [DDoS](DDoS.md) attacks.
* A DDoS attack against a DNS server can cause it to crash, rendering the users who rely on the sever unable to browse the web (users will still be able to reach recently visited websites if the DNS record is saved in a local cache).

## Scripts

* [Hijack local DNS](https://github.com/tymyrddin/ymrir/tree/master/dns_spoofer)