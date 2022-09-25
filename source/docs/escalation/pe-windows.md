# Privilege escalation on Windows

## Attack tree

```text
1 Privilege escalation Windows
    1.1 Manipulate access token (OR)
        1.1.1 Duplicate an access token and assign the token to a thread
        1.1.2 Create a new process with an impersonated token
        1.1.3 Leverage username and password to create a token
    1.2 Bypass user account control (UAC) (OR)
        1.2.1 Disabled UAC (OR)
        1.2.2 Admin privileges granted to the user by being in the local group “Administrators”
    1.3 DLL search order hijacking
        1.3.1 Replace an existing DLL or modify a .manifest or .local redirection file, directory, or junction (OR)
        1.3.2 Perform search order DLL hijacking on a vulnerable program that has a higher privilege level (AND)
        1.3.3 Cover the attack by loading the legitimate DLLS together with the new DLLs
    1.4 Other privilege escalation
```

## Notes

* In horizontal privilege escalation an adversary expands privileges by taking over another account.
* In vertical privilege escalation an attacker attempts to gain more permissions or access with an existing compromised account.

## Cheatsheets

* [Post-Exploitation-Cheat-Sheet](https://github.com/kmkz/Pentesting/blob/master/Post-Exploitation-Cheat-Sheet)