# Discover application vulnerabilities

## Attack tree

```text
1 Known Vulnerabilities (AND)
    1.1 Look up in Exploit databases
2 Latent vulnerabilities (AND)
    2.1 Code reviews 
    2.2 Code scanning
3 New vulnerabilities
    3.1 Root cause analysis
    3.2 Variant analysis
    3.3 Patch analysis
    3.4 Exploit technique analysis
```

## Notes

* Known vulnerabilities are the simplest vulnerabilities which have been discovered and disclosed. These are often found in the libraries and frameworks that are part of an application. These vulnerabilities tend to get hit very quickly (hours) after disclosure by automated attacks from all over the world, so response speed is critical.
* Latent vulnerabilities are instances of typical vulnerability classes.: buffer overflows, cross-site scripting (XSS) and SQL injection for example.These vulnerabilities are not listed in databases -- these are unique to each application. 
* New vulnerabilities represent a new class of vulnerability. These appear at a slow rate, maybe one or two per year. After discovery, research and confirmations, these turn into latent vulnerabilities. There is a learning curve on these new vulnerabilities for attackers and defenders. This type of research is expensive and for most companies unlikely to produce much payoff in terms of overall risk reduction.

Use found [technologies used](Gather-app-information.md) to look up vulnerabilities. 

## Tools

* [Netcraft: Site Report](https://sitereport.netcraft.com/)
* [Offensive Security Exploit database](https://www.exploit-db.com/)
* [Rapid 7 Exploit database](https://www.rapid7.com/db/)

## Articles

* [0 days in the wild](https://googleprojectzero.github.io/0days-in-the-wild/)