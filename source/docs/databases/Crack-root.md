# Cracking the database root password

## Attack tree

```text
1 Cracking the database root password
    1.1 Try logging in as root with the default password
    1.2 Try common passwords
    1.3 Use a password auditing tool
        1.3.1 External - run DBPwAudit, Access Passview or specific other tool
        1.3.2 Internal (having an account on the server that hosts the database) - run a hash cracker like John the Ripper against the database’s password file. The location of the hash file is different depending on the database.
    1.4 If it is Open Source Software, check the source code on the repository host.
```

## Tools

* [DBPwAudit](https://www.darknet.org.uk/2016/09/dbpwaudit-database-password-auditing-tool/), preinstalled in Kali

## Resources

* [Collected common password lists](https://github.com/danielmiessler/SecLists/tree/master/Passwords)

## Cheatsheets

* [MySQL enumeration](cheatsheets:docs/enumeration/mysql)
* [Brute-force MySQL](cheatsheets:docs/databases/brute-force)