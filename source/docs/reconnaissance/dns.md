# Gather DNS information

## Attack tree

```text
1 Use InterNIC (AND)
    1.1 from Registrars (AND)
    1.2 from other web sources (AND)
    1.3 from cli command
2 Gather wider
    2.1 Discover websites on the same server (AND)
    2.2 Discover subdomains (AND)
    2.3 Discover sensitive files
```

## Notes

* Use whois to gather Domain name, IP address, Administrative Details, autonomous system number, DNS

## Tools

* [WhoIs LookUp DomainTools](https://whois.domaintools.com/)
* [Robtex](https://www.robtex.com/)
* [DNSDumpster](https://dnsdumpster.com/)
* [Knockpy subdomains](https://github.com/guelfoweb/knock), already installed on Kali

## Cheatsheets

* [DNS registrars](cheatsheets:docs/reconnaissance/DNS-registrars)
* [Shodan](cheatsheets:docs/reconnaissance/Shodan-cheatsheet)
* [Shodan CLI](cheatsheets:docs/reconnaissance/Shodan-CLI-cheatsheet)
