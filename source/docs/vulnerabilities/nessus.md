# Vulnerability scanning with Nessus

## Attack tree

```text
1 Start a new scan (click the New Scan button in the top-right corner)
2 Choose template
    2.1 Host discovery: discover live systems on the network and open ports on those systems.
    2.2 Basic network scan: Vulnerability scan on systems using default settings and pre-defined plug-ins.
    2.3 Advanced scan: Customise what plug-ins the scan uses (which determines the vulnerabilities to check for).
        2.3.1 Set Name, Description and Targets.
        2.3.2 Add usernames and passwords for credentialed scans.
        2.3.3 Enable or disable plug-ins.
    2.4 Malware scan: Scans remote Windows and Linux systems to see if there is malware present on the systems.
    2.5 Web application tests: Assess common vulnerabilities found in websites.
    2.6 Internal PCI network scan: Example of a compliance template for PCI DSS regulations.
3 Launch the scan
4 View results
```

## Example

![Nessus results](../../_static/images/nessus-results.png)

## Tools

* [Nessus Essentials](https://www.tenable.com/products/nessus/nessus-essentials)