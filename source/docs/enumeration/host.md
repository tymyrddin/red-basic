# Host enumeration

## Attack tree

```text
1 Enumerate
    1.1 Users
    1.2 Groups
    1.3 Network shares with SMBMap or nmap
    1.4 URLs with w3af, Burpsuite or nmap
    1.5 Services
```

# Examples

Try to enumerate users, or list the users:

    nmap --script smb-enum-users.nse [ip_or_hostname]

Try to enumerate the groups on a system:

    nmap --script smb-enum-groups.nse [ip_or_hostname]

Network shares (download script first):

    nmap --script smb-enum-shares.nse [ip_or_hostname]

URLs/Web pages:

    nmap --script http-enum.nse [ip_or_hostname]

Services:

    nmap --script smb-enum-services.nse [ip_or_hostname]

## Tools

* [SMBMap](https://tools.kali.org/information-gathering/smbmap)
* [w3af](http://w3af.org) 
* [BurpSuite](https://portswigger.net/burp)