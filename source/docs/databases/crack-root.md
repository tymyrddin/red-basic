# Cracking the database root password

## Attack tree

```text
1 Cracking the database root password
    1.1 Try logging in as root without password and with default passwords
    1.2 Try common passwords
    1.3 Use a brute forcing tool
        1.3.1 External - run a tool
        1.3.2 Internal (having an account on the server that hosts the database) - run a hash cracker like John the Ripper against the database’s password file. The location of the hash file is different depending on the database.
    1.4 If it is Open Source Software, check the source code on the repository host.
```

## Tools

* [Metasploit framework](https://www.kali.org/tools/metasploit-framework/)
* [Hydra](https://www.kali.org/tools/hydra/)
* [Medusa](https://www.kali.org/tools/medusa/)
* [Patator](https://www.kali.org/tools/patator/)
* [Ncrack](https://www.kali.org/tools/ncrack/)

## Resources

* [Collected common password lists](https://github.com/danielmiessler/SecLists/tree/master/Passwords)

## Cheatsheets

* [Databases enumeration](cheatsheets:docs/enumeration/databases)
* [Brute-force databases](cheatsheets:docs/databases/brute-force)