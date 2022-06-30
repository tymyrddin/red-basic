# Service and OS detection

## Attack tree

```text
1 Detect Operating Systems (AND)
2 Detect services (AND)
3 Grab banner
```
## Notes

Service and OS detection use different methods to determine the operating system or service running on a particular port.

## Examples

```text
# nmap -sn -T4 -oG Discovery.gnmap 192.168.1.1/24
# grep “Status: Up” Discovery.gnmap | cut -f 2 -d ‘ ‘ > LiveHosts.txt
```

## Cheatsheets

* [Nmap cheatsheet](cheatsheets:docs/scanning/Nmap-cheatsheet)
* [Nessus](cheatsheets:docs/scanning/Nessus-cheatsheet)
* [Metasploit cheatsheet](https://assets.contentstack.io/v3/assets/blt36c2e63521272fdc/blt2666925c05bfae0c/5e34a63e07e2907e353a2f5b/metasploit-cheat-sheet-2.pdf)
* [Unicornscan cheatsheet](cheatsheets:docs/scanning/Unicornscan-cheatsheet)
* [IKE-scan cheatsheet](cheatsheets:docs/scanning/IKE-scan-cheatsheet)



