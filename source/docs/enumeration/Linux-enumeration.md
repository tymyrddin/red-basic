# Linux enumeration

## Attack tree

```text
1 Get information from
    1.1 Settings: Users and usernames (AND)
    1.2 Applications: some run on defaults, or there may be null or blank passwords (AND)
    1.3 Permissions on key directories and files (AND)
    1.4 Shares if linux shares resources over the network (AND)
    1.5 Samba, the linux equivalent to smb, may give information about the windows network and its shares (AND)
    1.6 NFS information can give information on permissions and the network services (AND)
    1.7 network services such as DNS, LDAP, SMTP, etc (AND)
    1.8 various built-in commands and utilities
```

## Resources

* [LinEnum](https://github.com/rebootuser/LinEnum) is a basic shell script that performs over 65 checks, getting anything from kernel information to locating possible escalation points such as potentially useful SUID/GUID files and Sudo/rhost mis-configurations and more.
* [enum4linux](https://labs.portcullis.co.uk/tools/enum4linux/) is a linux alternative to enum.exe for enumerating data from Windows and Samba hosts. It is a wrapper around the Samba tools smbclient, rpclient, net and nmblookup 
* [Netcat](https://sectools.org/tool/netcat/) is network debugging and investigation tool that can assist with port scanning, transferring files, and port listening, and it can also be used as a backdoor. 
* [OpenVAS](https://www.openvas.org/)
* [NMap](https://nmap.org/) 

