# Fingerprint webserver

## Attack tree

```text
1 Gather information such as server name, server type, operating systems, applications running on the server, etc.
```

## Tools

* [Netcraft: Search Web by Domain](https://searchdns.netcraft.com/)
* [recon-ng](https://www.kali.org/tools/recon-ng/)

## Mitigations

* [Hide Apache version and OS identity](webserver-mitigations:docs/apache/hide-info)
* [Hide Nginx version and OS identity](webserver-mitigations:docs/nginx/hide-info)