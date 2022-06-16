# Unauthorised privilege escalation on a web server

## Attack tree

```text
    1 Upload the web-shell (AND)
        1.1 SQL injection
        1.2 Remote file inclusion (RFI)
        1.3 FTP
        1.4 Cross-site scripting (XSS) as part of a social engineering attack 
        1.5 Other
    2 Escalate privileges on host 
```

## Notes

A web-shell is a web script that is placed on an openly accessible web server to allow an adversary to use the web server as a gateway into a network. A web-shell may provide a set of functions to execute or a command-line interface on the system that hosts the web server. In addition to a server-side script, a web-shell may have a client interface program that is used to talk to the web-server. It usually contains a backdoor which allows an attacker to remotely access and possibly, control a server at any time. This would save the attacker the inconvenience of having to exploit a vulnerability each time access to the compromised server is required.

A web-shell can be used for monitoring (sniffing) the network traffic on the system, scanning the internal network to discover live hosts, and enumerating firewalls and routers within the network. Another use of web-shells is to make servers part of [a botnet](../social-engineering/Create-a-botnet.md). Using a web-shell, an attacker can attempt to perform privilege escalation attacks by exploiting local vulnerabilities on the system in order to assume root privileges.
