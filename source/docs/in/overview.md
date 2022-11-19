# Creating malware

* A backdoor is a file that gives full control over the machine ([Windows](windows.md), [Linux](linux.md), [macOS](macos.md)) that it gets executed on.
  * Backdoors can be caught by antivirus programs.
* A [keylogger](keylogger.md) is a program that records keys pressed on the keyboard.
  * Runs in the background of target system.
  * Reports every key pressed on the target machine to email.
  * Starts with system boot, hence can be caught by antivirus programs.
* A [password recovery tool](pwrecovery.md) can be used as a post exploitation tool to retrieve saved passwords on local computer. It needs to be executed on target computer and displays logs on screen or stores them in a local file. Find one that:
  * Recovers saved passwords from lots of programs.
  * Recovers passwords from memory.
  * Works with Windows and Linux.
  * Displays result on screen or stores it on local machine.
* A [trojan](trojan-windows.md) presents itself as a useful legitimate program so that users could get fascinated by it and install it. It usually tricks users by using social engineering techniques. For example:
  * Download backdoor + keylogger.
  * Download keylogger + password recovery tool.
  * Download keylogger + password recover tool + backdoor.
  * Use it as a trojan -- evil file + a normal file.

## Attack tree

```text
1 Create payload (AND)
    1.1 Backdoor
    1.2 Keylogger
    1.3 Password recovery tool
    1.4 Trojan
    1.5 ...
4 Download to & execute payloads on target machine
```

## Cheatsheets

* [Payloads All The Things](https://github.com/swisskyrepo/PayloadsAllTheThings)
