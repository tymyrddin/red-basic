# Gain unauthorised access

## Attack tree

```text
    1 Gain credentials of an authorised user in a vulnerable physical context (OR)
        1.1 Ask for a temporary use of password from an already authorised user (OR)
        1.2 Cooperate with an already authorised user to receive credentials (OR)
        1.3 Fool an authorised user to leak credentials (OR)
        1.4 Shoulder surfing (OR)
        1.5 Install and use keylogger (OR)
        1.6 Implant other malware for further remote intrusions (OR)
        1.7 Use an unattended logged-in machine (OR)
        1.8 Steal devices containing credentials of authorised users (OR)
        1.9 Steal devices or storage containing the information 
    2 Capture authorised user credentials via vulnerable web application (OR)
        2.1 Phishing (OR)
        2.2 Pharming (OR)
        2.3 Credential stuffing 
    3 Password-based attacks (OR)
        3.1 Publicly available information (OR)
            3.1.1 Reconnaissance for guessing user names (AND)
            3.1.2 Crack password
                3.1.2.1 Brute-force password (OR)
                3.1.3.2 Dictionary attack
    4 Steal credentials via vulnerable network
        4.1 Network reconnaissance (AND)
            4.1.1 Find where the resources are logically located (AND)
            4.1.2 Scan the network for alive hosts (AND)
            4.1.3 Probe ports to discover services (AND)
            4.1.4 Know, learn or research the vulnerabilities of OSs and the applications they run
        4.2 Exploit vulnerability (AND)
        4.3 Vulnerable host (OR)
            4.3.1 Compromise server (AND)
            4.3.2 Retrieve password files
                4.3.2.1 View unencrypted password files (OR)
                4.3.2.2 Decrypt password files
        4.4 Sniff network management traffic (AND)
        4.5 Capture password from router configuration (OR)
            4.5.1 Compromise router (AND)
                4.5.1.1 View unencrypted router configuration (OR)
                4.5.1.2 Decrypt encrypted router configuration
        4.6 Intercept or modify data with a MitM attack
    5 Discover implementation flaw in (access control) protocol
    6 Discover new attack 
```

## Notes

Use, disclosure, alteration, and destruction of information, including gaining access to the network to gain access to the information and/or gaining access to the building with the devices the information resides on. In the context of network attacks, the first objective of an adversary is to gain initial access, so additional reconnaissance can be done to scout out resources, IP addresses, and perhaps even a network discovery (mapping) program or a sniffer-type packet-capturing utility, to capture administrative-level passwords.
