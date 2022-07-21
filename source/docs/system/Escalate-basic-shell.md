# Upgrade basic shell access to meterpreter/empire access

## Attack tree

```text
1 Basic shell access
2 Go to /tmp/ directory on the target machine
3 curl or wget file (in this case empire or meterpreter shell) from apache2 server on Kali machine to the target machine
4 Start matching listener on Kali
5 Execute the downloaded shell on the target machine
6 Post exploitation
```

## Notes

* For Windows: [Upgrading shells to Meterpreter](https://docs.metasploit.com/docs/pentesting/metasploit-guide-upgrading-shells-to-meterpreter.html)

## Cheatsheets

* [Linux post exploitation enumeration](cheatsheets:docs/enumeration/linux-post)
* [Windows post exploitation enumeration](cheatsheets:docs/enumeration/windows-post)
* [Spawning a TTY Shell](https://netsec.ws/?p=337) (when using `nc`)

