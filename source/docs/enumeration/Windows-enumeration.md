# Windows enumeration

## Attack tree

```text
1 Get information
    1.1 Usernames
    1.2 Default configurations
    1.3 Default passwords
    1.4 Domain names
    1.5 Computer names
    1.6 Shares
    1.7 Windows information
    1.8 Network information like DNS, SMTP, SNMP information
    1.9 Application details
    1.10 Banners
    1.11 Routing tables
```

## Notes

NetBIOS is outdated but still lives on in some older systems, sometimes for backward compatability. It is the equivalent of broadcasting names to look for each other but is not routable. It is local network only. If no one on the other network can use it for your network, then no one there can access your NetBIOS shared folders and printers, unless one has gained access to your local network. You can also access NetBIOS machines with a WINS server. That is the NetBIOS equivalent of a DNS server.

## Tools
 
* [Net commands](https://www.computerhope.com/nethlp.htm) can be used to glean almost any aspect of a local network and its settings including network shares, network printers and print jobs, network users, policies!, etc. It is available from within the Command Prompt in all Windows operating systems including Windows 10, Windows 8, Windows 7, Windows Vista, Windows XP, and further back. The availability of certain net command switches and other net command syntax may differ from operating system to operating system. 
* [WinFingerprint](https://www.softpedia.com/get/Security/Security-Related/winfingerprint.shtml) is a Win32 MFC VC++ .NET based security tool that is able to Determine OS, enumerate users, groups, shares, SIDs, transports, sessions, services, service pack and hotfix level, date and time, disks, and open tcp and udp ports. It is GUI-based and you can use checkboxes to indicate which information is desired. 
* [Nbtstat](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/nbtstat) shows NetBIOS statistics. It is not that important, but if you are enumerating from within, on a network which includes older boxes, it has its use.
* [NMap](https://nmap.org/)

## Cheatsheets

* [Windows enumeration cheatsheet](cheatsheets:docs/enumeration/windows)


