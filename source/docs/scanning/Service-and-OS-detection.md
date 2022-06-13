# Service and OS detection

Service and OS detection use different methods to determine the operating system or service running on a particular port.

## Attack tree

```
1 Detect Operating Systems (AND)
2 Detect services (AND)
3 Grab banner
```

## Examples

```
# nmap -sn -T4 -oG Discovery.gnmap 192.168.1.1/24
# grep “Status: Up” Discovery.gnmap | cut -f 2 -d ‘ ‘ > LiveHosts.txt
```

## Resources

* [Nmap cheatsheet](https://github.com/tymyrddin/nest-egg/blob/main/cheatsheets/Nmap-cheatsheet.md)
* [Nessus](https://github.com/tymyrddin/nest-egg/blob/main/cheatsheets/Nessus-cheatsheet.md)
* [Metasploit cheatsheet](https://github.com/tymyrddin/nest-egg/blob/main/guides/Metasploit-cheatsheet.pdf)
* [Unicornscan cheatsheet](https://github.com/tymyrddin/nest-egg/blob/main/cheatsheets/Unicornscan-cheatsheet.md)
* [IKE-scan cheatsheet](https://github.com/tymyrddin/nest-egg/blob/main/cheatsheets/IKE-scan-cheatsheet.md)




