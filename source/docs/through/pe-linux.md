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

### Kernel exploits

A failed kernel exploit can lead to a system crash. Make sure this potential outcome is acceptable within the scope of 
the penetration testing engagement before attempting a kernel exploit. 

Kernel exploit methodology:

1. Identify the kernel version
2. Search and find an exploit code for the kernel version of the target system
3. Run the exploit

You can transfer the exploit code from your machine to the target system using the SimpleHTTPServer Python module and 
wget respectively. 

### Sudo exploits

The `sudo` command, by default, allows for running a program with root privileges. System administrators sometimes 
give regular users some flexibility on their privileges. For example, a junior SOC analyst may need to use Nmap 
but would not be cleared for full root access. The system administrator can allow this user to only run Nmap with 
root privileges while keeping its regular privilege level throughout the rest of the system.

Any user can check its current situation related to root privileges using the `sudo -l` command.

Use GTFObins for gathering information on how any program, on which a user may have sudo rights, can be used. 

### SUID exploits

SUID (Set-user Identification) and SGID (Set-group Identification) allow files to be executed with the 
permission level of the file owner or the group owner, respectively.

Such files have an `s` bit set showing their special permission level. To find binaries known to be exploitable 
when the SUID bit is set see [GTFObins SUID](https://gtfobins.github.io/#+suid).

### Capabilities exploits

Another method system administrators can use to increase the privilege level of a process or binary is by capabilities. 
Capabilities help manage privileges at a more granular level. If a SOC analyst needs to use a tool that needs to 
initiate socket connections, the capabilities of the binary can be changed such that it would get through its task 
without needing a higher privilege user.

## Tools

* [LinEnum](https://github.com/rebootuser/LinEnum)
* [PEASS-ng](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS) is a script that searches for possible paths to escalate privileges on Linux/Unix* hosts. It also enumerates the system.
* [Linux Exploit Suggester 2](https://github.com/jondonas/linux-exploit-suggester-2) returns a list of possible CVEs, exploits, and exploit POCs (Proof of Concept) for the running Linux kernel.
* [Traitor](https://github.com/liamg/traitor) takes advantage of local misconfigurations and vulnerabilities (including most of GTFOBins) in order to pop a root shell. These are primarily misconfigurations, not exploits.

## Resources

* [GTFOBins](https://gtfobins.github.io/) is a curated list of Unix binaries that can used to bypass local security restrictions in misconfigured systems.
