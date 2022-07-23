# Discover vulnerabilities

## Attack tree

```text
1 Port scanning (AND)
    1.1 TCP scans (OR)
            1.1.2 Use the default SYN (-sS) scans (privileges are required) (OR)
            1.1.3 Use the connect (-sT) scan (privileges are not required)
    1.2 UDP scans
2 Check for potential known problems and vulnerabilities with found ports
```
## Notes

* There are many ports scanners that all operate in pretty much the same way. 
* The most common type of scan in the discovery phase is a `SYN` scan (or SYN stealth scan), named for the `TCP SYN` flag used in the `TCP` connection sequence. To perform the default SYN (`-sS`)scans, privileges are required. If privileges are insufficient a TCP connect (`-sT`) scan is used. 
* The [Ports Database](https://www.speedguide.net/ports.php) is a comprehensive, searchable database of official and unofficial tcp/udp port assignments, known vulnerabilities, trojans, applications use and more.

## Cheatsheets

* [Port scanning cheatsheet](cheatsheets:docs/scanning/Port-scanning-cheatsheet)
* [Ports cheatsheet](cheatsheets:docs/scanning/Ports-cheatsheet)
* [Nmap cheatsheet](cheatsheets:docs/scanning/Nmap-cheatsheet)

### Alternatives
* [Nessus cheatsheet](cheatsheets:docs/scanning/Nessus-cheatsheet)
* [Metasploit cheatsheet](https://assets.contentstack.io/v3/assets/blt36c2e63521272fdc/blt2666925c05bfae0c/5e34a63e07e2907e353a2f5b/metasploit-cheat-sheet-2.pdf)
* [Unicornscan cheatsheet](cheatsheets:docs/scanning/Unicornscan-cheatsheet)
* [Ports cheatsheet](cheatsheets:docs/scanning/Ports-cheatsheet)
* [IKE-scan cheatsheet](cheatsheets:docs/scanning/IKE-scan-cheatsheet)
