# Keylogger

Installing a separate keylogger which emails the results can be a good idea (depending on context and chosen strategy). 
For example, when hacking the target itself is not of interest, but passwords are, using just a keylogger like Zlogger
can save a lot of time and effort.

## Attack tree

```text

1 Create keylogger
    1.1 Standalone (for example Zlogger)
        1.1.1 Set parameters and generate
        1.1.2 Create gmail account with app password (in Security section)
    1.2 Metasploit 
    1.3 Powershell 
2 Copy file to /var/www/html/evil-files (or other server location)
```
## Notes

Remove ZLogger: 
* Start -> regedit -> `Computer\HKEY_CURRENT_USER\Software\Microsoft\Windows\Current\Version\Run` => 
Right click => Modify (copy path to actual executable), then delete the `<keylogger name>` entry. 
* In task manager end the associated task
* In file manager paste the just copied path and delete the executable.

## Tools

* [ZLogger](https://github.com/z00z/ZLogger)
* [Using a Keylogger with Metasploit](https://www.offensive-security.com/metasploit-unleashed/Keylogging/)