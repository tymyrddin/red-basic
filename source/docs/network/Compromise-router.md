# Compromise router

## Attack tree

```text
    1 Gain physical access to router
        1.1 Gain physical access to building (AND)
        1.2 Guess passwords (OR)
        1.3 Try password recovery
    2 Gain logical access to router
        2.1 Compromise network manager system
            2.1.1 Exploit application layer vulnerability (OR)
            2.1.2 Hijack management traffic
        2.2 Login to router (OR)
            2.2.1 Guess password (OR)
            2.2.2 Sniff password (OR)
            2.2.3 Hijack management session
                2.2.3.1 Telnet (OR)
                2.2.3.2 SSH (OR)
                2.2.3.3 SNMP (OR)
            2.2.4 Social engineering
        2.3 Exploit implementation flaw in protocol/application in router
            2.3.1 Telnet (OR)
            2.3.2 SSH (OR)
            2.3.3 SNMP (OR)
            2.3.4 Proprietary management protocol 
```

## Tools

* [Router Exploitation Toolkit (REXT)](https://github.com/j91321/rext)
* [Router Pwn](http://routerpwn.com/)

