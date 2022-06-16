# Unauthorised privilege escalation on hosts

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
    2 Become root on Linux
        2.1 Kernel exploit (OR)
            2.1.1 Detect vulnerabilities (AND)
            2.1.2 Develop or acquire exploit code (AND)
            2.1.3 Transfer the exploit to the target machine (AND)
            2.1.4 Execute the exploit on the target
        2.2 Exploit sudo
            2.2.1 Find which commands current user is allowed to use (sudo -l) (AND)
            2.2.2 Exploit the parameters of a command that is allowed to be executed with root permissions
                2.2.2.1 sudo find /etc/passwd -exec /bin/sh \; (OR)
                2.2.2.2 sudo vim -c '!sh' (OR)
                2.2.2.3 sudo awk 'BEGIN {system(“/bin/sh”)}' (OR)
                2.2.2.4 Other commands that are allowed to be executed with root permissions to invoke a shell
        2.3 Other privilege escalation
```

## Notes

* In horizontal privilege escalation an adversary expands privileges by taking over another account.
* In vertical privilege escalation an attacker attempts to gain more permissions or access with an existing compromised account.
