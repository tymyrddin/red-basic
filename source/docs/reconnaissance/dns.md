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

### Use nslookup

    nslookup www.target.com

Setting the type of query to MX (mail exchange) records:

```text
nslookup
set type=MX
target.com
```

Then use `nslookup` again to resolve the FQDNs of the mail servers to IP adressess.

Try a DNS zone transfer:

```text
nslookup
server <ip_or_fqdn_of_target_DNS_server>
set type=all
ls -d <target_domainname>
```

If successful, make a note of it and add it to the remediation list in the pentest report.

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

Try a zone transfer with dig:

    dig target.com axfr

### Use recon-ng

Get started with a target by creating a workspace for it:

```text
recon-ng
workspaces add <target>
```

Add the domain names and company names to the recon-ng database tables for use in further commands:

```text
add domains target.com
add domains www.target.com
add domains othertarget.com
add domains www.othertarget.com

add companies Target Name~A whatever company
add companies Target Subsidiary~A subsidiary company
add companies Product Target ~A whatever company product line
```

To view the domains and company tables:

```text
show companies
show domains
```

Collect the points of contact from Whois databases:

```text
use recon/domains-contacts/whois_pocs
run
```

Discover other domain names and hosts on the Internet related to the target by using a Bing search and a Google search:

```text
use recon/domains-hosts/bing_domain_web
run
use recon/domains-hosts/google_site_web
run
```

Load the reporting module and specify the creator of the report, the customer, and the report filename to generate:

```text
use reporting/html
set CREATOR 'Pentester name'
set CUSTOMER 'Target Name'
set FILENAME /root/Desktop/target_recon.html
run
```

If we had used other modules to collect additional information, that information would have been included in the 
report. As shown in the help menu the Marketplace: Interfaces with the module marketplace to pick and choose 
modules you want. 

```text
marketplace
marketplace install modulename
modules load modulename
[modulename] > show options
[modulename] > options set option
[modulename] > info
[modulename] > input
[modulename] > run
```

## Tools

* [WhoIs LookUp DomainTools](https://whois.domaintools.com/)
* [Robtex](https://www.robtex.com/)
* [DNSDumpster](https://dnsdumpster.com/)
* [Knockpy subdomains](https://github.com/guelfoweb/knock), already installed on Kali
* [Dirb](https://www.kali.org/tools/dirb/), already installed on Kali, to brute-force find sensitive files
* [Maltego](https://www.maltego.com), preinstalled in kali
* [Recon-ng](https://tools.kali.org/information-gathering/recon-ng)
* [Infosec institute: Awesome modules of Recon-ng used for Web Recon testing](https://resources.infosecinstitute.com/topic/awesome-modules-of-recon-ng-used-for-web-recon-testing/)

## Cheatsheets

* [DNS registrars](cheatsheets:docs/reconnaissance/DNS-registrars)
* [Shodan](cheatsheets:docs/reconnaissance/Shodan-cheatsheet)
* [Shodan CLI](cheatsheets:docs/reconnaissance/Shodan-CLI-cheatsheet)
