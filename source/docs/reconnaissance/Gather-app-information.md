# Gathering application information

## Attack tree

```text
1 Find info about the owner of the target (AND)
2 Discover technologies used on the target (AND)
3 Gather info about each public-facing website of the target
```

## Notes

Use [search engines](Search-engines.md), [DNS tools](Deep-dive-DNS.md) to discover IP addresses, 
domain name information, technologies used, other websites on the same server, DNS records, unlisted files, 
sub-domains, directories, neighbours, ...

## Tools

* [Netcraft: Site Report](https://sitereport.netcraft.com/)
* [Netcraft: Search Web by Domain](https://searchdns.netcraft.com/)
* [Netcraft: Site's neighbours](https://sitereport.netcraft.com/netblock)
* [Bing search engine](https://www.bing.com/), use `ip:<IP address>` as search term to find neighbours
* [Dirb](https://www.kali.org/tools/dirb/), already installed on Kali, to brute-force find sensitive files
* [Maltego](https://www.maltego.com), preinstalled in kali

## Scripts

* [Simple crawler](https://github.com/tymyrddin/reomais/blob/main/crawler)
* [Simple spider](https://github.com/tymyrddin/reomais/blob/main/spider)



