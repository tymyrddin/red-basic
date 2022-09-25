# Exploit remote code execution vulnerabilities

## Attack tree

```text
1 Netcat installed on both systems (hacking and target machines) (OR)
    1.1 Install netcat on both systems
    1.2 Create a reverse shell (for example with weevely)
    1.3 Setup a netcat listener on the hacking machine
    1.4 Connect to the listener from the target machine
    1.5 Post exploitation
2 Netcat only available on the target machine
    2.1 Install netcat on hacking machine and discover an existing option on target 
    2.2 Create a reverse shell 
    2.3 Setup a netcat listener on the hacking machine
    2.4 Connect to the listener from the target machine (see cheatsheet reverse shell commands)
    2.5 Post exploitation
```

## Notes

A reverse shell is a shell initiated on a target machine making it a server sending back to the adversaries' machine, 
which is now a client in a listening state waiting to pick up the shell.

Setting up a reverse shell with Netcat installed on both the hacking and target machine is easy. Unfortunately, most of 
the time, a target does not have Netcat installed on their system, and other means are required to launch a reverse 
shell. We can still set one up using Bash, Python, Perl, Ruby, PHP.

## Tools
* [Netcat](https://sectools.org/tool/netcat/)

## Scripts
* [Netcat replace](https://github.com/tymyrddin/ymrir/tree/master/netcat_replace)

## Cheatsheets
* [Reverse shell commands](cheatsheets:docs/application/reverse-shell-commands)
* [Weevely cheatsheet](cheatsheets:docs/payloads/weevely)
* [MSFvenom cheatsheet](https://www.offensive-security.com/metasploit-unleashed/Msfvenom/)

## Mitigations
* [Code execution](app-mitigations:docs/coding/rce)