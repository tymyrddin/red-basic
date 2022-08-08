# macOS enumeration

## Attack tree

```text
1 Get information from
    1.1 Settings: Users and usernames (AND)
    1.2 Applications: some run on defaults, or there may be null or blank passwords (AND)
    1.3 Permissions on key directories and files (AND)
    1.4 Shares if macOS shares resources over the network (AND)
    1.5 Samba, the linux equivalent to smb, may give information about the windows network and its shares (AND)
    1.6 NFS information can give information on permissions and the network services (AND)
    1.7 Network services such as DNS, LDAP, SMTP, etc (AND)
    1.8 Various built-in commands and utilities
```

## Tools

* [SwiftBelt](https://github.com/cedowens/SwiftBelt)