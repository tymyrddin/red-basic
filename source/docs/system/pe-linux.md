# Privilege escalation on Linux

## Attack tree

```text
2 Become root on Linux
    2.1 Find an exploit (software bug) in the operating system or other system services, for example a kernel exploit (OR)
        2.1.1 Detect vulnerabilities (AND)
        2.1.2 Develop or acquire exploit code (AND)
        2.1.3 Transfer the exploit to the target machine (AND)
        2.1.4 Execute the exploit on the target
    2.2 Find a misconfiguration in an existing legitimate tool, for example sudo
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

## Tools

* [LinEnum](https://github.com/rebootuser/LinEnum)
* [PEASS-ng](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS) is a script that searches for possible paths to escalate privileges on Linux/Unix* hosts. It also enumerates the system.
* [Linux Exploit Suggester 2](https://github.com/jondonas/linux-exploit-suggester-2) returns a list of possible CVEs, exploits, and exploit POCs (Proof of Concept) for the running Linux kernel.
* [GTFOBins](https://gtfobins.github.io/) is a curated list of Unix binaries that can used to bypass local security restrictions in misconfigured systems.
* [Traitor](https://github.com/liamg/traitor) takes advantage of local misconfigurations and vulnerabilities (including most of GTFOBins) in order to pop a root shell. These are primarily misconfigurations, not exploits.


## Cheatsheets

* [Linux post exploitation enumeration](cheatsheets:docs/enumeration/linux-post)