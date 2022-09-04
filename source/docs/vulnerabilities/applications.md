# Discovering more vulnerabilities

## Attack tree

```text
1 Known vulnerabilities (AND)
    1.1 Look up in Exploit databases
    1.2 Vulnerability scanning
2 Latent vulnerabilities (AND)
    2.1 Security code reviews 
    2.2 Specific code scanning for vulnerabilities
3 New vulnerabilities
    3.1 Root cause analysis
    3.2 Variant analysis
    3.3 Patch analysis
    3.4 Exploit technique analysis
```
## Notes

### Manual security code reviews

Manual security code reviews are usually performed by developers or security experts. Such efforts usually take place 
during a security push or pentesting engagement and are associated with a final security review. Coding errors can be 
found using different approaches, but even when compared to sophisticated tools, manual code reviews have clearly 
proven their value in the areas of precision and quality. Unfortunately, manual code reviews are also the most 
expensive to execute. It is important the developers are not part of the team that created the code, and a 
facilitator/security professional is also a good idea.

### New vulnerabilities

New vulnerabilities are usually found through bug bounty programs, or researched by dedicated groups like 
Google Project Zero.

## Resources known vulnerabilities

* [0-days In-the-Wild](https://googleprojectzero.github.io/0days-in-the-wild/)
* [Blackhat 2020: Reversing the Root (pdf of slides)](https://i.blackhat.com/USA-20/Wednesday/us-20-Stone-Reversing-The-Root-Identifying-The-Exploited-Vulnerability-In-0-Days-Used-In-The-Wild.pdf)

## Cheatsheets

* [Exploits databases](cheatsheets:docs/enumeration/exploits-dbs)

