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
    2 Gain access to the data stored in databases (OR)
        2.1 Using an SQL injection (OR)
        2.2 Using known database exploits
    3 Capture authorised user credentials via vulnerable web application (OR)
        3.1 Exploit file upload vulnerabilities (OR)
        3.2 Exploit remote code execution vulnerabilities (OR)
        3.3 Cross site scripting (XSS) (OR)
        3.4 Manipulating cookies (OR)
        3.5 Clickjacking (OR)
        3.6 Cross-Site Request Forgery (CSRF) 
    4 Gain access to webserver
        4.1 Hijacking session 
    5 Social engineering for delivering malware (OR)
        5.1 Email spoofing (OR)
        5.2 Steal access info with fake login page (OR)
        5.3 (Fake) Webpage with a hook (OR)
        5.4 SEO poisoning (OR)
        5.5 All kinds of creative ways to lure people 
    6 Password-based attacks on applications, databases, user accounts (OR)
        6.1 Publicly available information (OR)
            6.1.1 Reconnaissance for guessing user names (AND)
            6.1.2 Crack password
                6.1.2.1 Brute-force password (OR)
                6.1.3.2 Dictionary attack
    7 Steal credentials via vulnerable network
        7.1 Network reconnaissance (AND)
            7.1.1 Find where the resources are logically located (AND)
            7.1.2 Scan the network for alive hosts (AND)
            7.1.3 Probe ports to discover services (AND)
            7.1.4 Know, learn or research the vulnerabilities of OSs and the applications they run
        7.2 Exploit vulnerability (AND)
        7.3 Vulnerable host (OR)
            7.3.1 Compromise server (AND)
            7.3.2 Retrieve password files
                7.3.2.1 View unencrypted password files (OR)
                7.3.2.2 Decrypt password files
        7.4 Sniff network management traffic (AND)
        7.5 Capture password from router configuration (OR)
            7.5.1 Compromise router (AND)
                7.5.1.1 View unencrypted router configuration (OR)
                7.5.1.2 Decrypt encrypted router configuration
        7.6 Intercept or modify data with a MitM attack
    8 Discover implementation flaw in (access control) protocol
    9 Discover new attack (vector)
```

## Notes

Use, disclosure, alteration, and destruction of information, including gaining access to the network to gain access to the information and/or gaining access to the building with the devices the information resides on. In the context of network attacks, the first objective of an adversary is to gain initial access, so additional reconnaissance can be done to scout out resources, IP addresses, and perhaps even a network discovery (mapping) program or a sniffer-type packet-capturing utility, to capture administrative-level passwords.
