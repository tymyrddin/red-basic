# Service and OS detection

## Attack tree

```text
1 Detect Operating Systems (AND)
2 Detect services
```
## Notes

Service and OS detection use different methods to determine the operating system or service running on a particular port.

## Examples

### Detect services

```text
# nmap -sV -T4 -Pn -oG ServiceDetect -iL $TARGETFILE
```

### OS detection

```text
# nmap -O -T4 -Pn -oG OSDetect -iL $TARGETFILE        
```

## Cheatsheets

* [Nmap cheatsheet](cheatsheets:docs/scanning/Nmap-cheatsheet)

## Mitigations

* [Hide Apache version and OS identity](webserver-mitigations:docs/apache/hide-info)
* [Hide Nginx version and OS identity](webserver-mitigations:docs/nginx/hide-info)