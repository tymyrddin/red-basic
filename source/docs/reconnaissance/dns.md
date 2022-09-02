# DNS profiling

## Attack tree

```text
1 Use InterNIC (AND)
    1.1 from Registrars (AND)
    1.2 from other web sources (AND)
    1.3 from cli command
2 Gather wider
    2.1 Discover websites on the same server (AND)
    2.2 Discover subdomains (AND)
    2.3 Discover email addresses (AND)
    2.4 Discover sensitive files
```

## Notes

* Use whois to gather Domain name, IP address, Administrative Details, autonomous system number, DNS

## Examples

### Use a whois search

* Go to `www.arin.net/whois` and search for <target name> in the ARIN Whois/RDAP Search bar.
* Find a handle which displays more information about this registration including the range of IP addresses.
* Find an entry with a net range (public IPs).
* Determine all the public IP blocks the target may have.

If you cannot find any results try some other Whois database search sites.

### Use theHarvester

Use theHarvester to collect email address and IP addresses of public systems for target.com:

    theharvester -d target.com -b all

### Use Shodan

* Go to `www.shodan.io`, register is you have not already.
* Use the Search box to search for the target.
* Scroll through the results.
* Choose the Maps tab to see the physical locations of those systems.
* Choose one of the red dots representing one of the systems to see the IP address and ports open on that system.
* Click the View Details button to view more information about that system.
* Investigate all systems on the map belonging to the target.

### Use dig

Use `dig` to perform DNS profiling of the target organisation.

To determine the IP address of a system:

    dig www.target.com +short

To determine the DNS servers:

    dig target.com NS +short

To determine the email servers for the organisation:

    dig target.com MX +short

## Tools

* [WhoIs LookUp DomainTools](https://whois.domaintools.com/)
* [Robtex](https://www.robtex.com/)
* [DNSDumpster](https://dnsdumpster.com/)
* [Knockpy subdomains](https://github.com/guelfoweb/knock), already installed on Kali
* [Dirb](https://www.kali.org/tools/dirb/), already installed on Kali, to brute-force find sensitive files
* [Maltego](https://www.maltego.com), preinstalled in kali

## Cheatsheets

* [DNS registrars](cheatsheets:docs/reconnaissance/DNS-registrars)
* [Shodan](cheatsheets:docs/reconnaissance/Shodan-cheatsheet)
* [Shodan CLI](cheatsheets:docs/reconnaissance/Shodan-CLI-cheatsheet)
