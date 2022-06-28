# Gather application information

## Attack tree

```
1 Find info about the owner of the target (AND)
2 Discover technologies used on the target (AND)
3 Gather info about each public-facing website of the target
    3.1 Discover websites on the same server
    3.2 Discover subdomains
    3.3 Discover sensitive files
```

## Notes

Use [search engines](Gather-public-information.md), [DNS tools](Gather-DNS-information.md) to discover IP addresses, 
domain name information, technologies used, other websites on the same server, DNS records, unlisted files, 
sub-domains, directories, neighbours, ...

## Tools

* [Netcraft: Site Report](https://sitereport.netcraft.com/)
* [Netcraft: Search Web by Domain](https://searchdns.netcraft.com/)
* [Netcraft: Site's neighbours](https://sitereport.netcraft.com/netblock)
* [Knock](https://github.com/guelfoweb/knock)

## Scripts

* [Simple crawler](https://github.com/tymyrddin/reomais/blob/main/crawler)
* [Simple spider](https://github.com/tymyrddin/reomais/blob/main/spider)



