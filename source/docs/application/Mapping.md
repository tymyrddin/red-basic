# Web application mapping

## Attack tree

```text
1 Find sensitive information and/or expose vulnerable functionalities (AND)
    1.1 Brute force common filenames 
    1.2 Brute force directories
2 Find insecure web applications (if any)
    2.1 Brute force subdomains
    2.2 Brute force hidden urls
```

## Notes

* When attacking a custom web application or large site, knowing all the files accessible on the web server can be 
very handy. To this end, a crawler can discover some web application info. To 
discover more of this content, like configuration files, leftover development files, debugging scripts, and other 
security breadcrumbs can provide sensitive information or expose functionality that software developers did not 
intend, is to use a brute-forcing tool.
* And it is not uncommon for a single web server to serve several web applications. If attacking the server, 
these other hostnames may give an easier way to get a shell. It is not rare to find an insecure web application, 
or even development resources, located on the same machine as the target. 

## Scripts

* [Simple crawler](https://github.com/tymyrddin/reomais/blob/main/crawler)
* [Simple spider](https://github.com/tymyrddin/reomais/blob/main/spider)
* [Mapping WordPress](https://github.com/tymyrddin/reomais/blob/main/mapping_wordpress)
* [Brute-Forcing directories and file locations](https://github.com/tymyrddin/reomais/blob/main/bf_locations)

