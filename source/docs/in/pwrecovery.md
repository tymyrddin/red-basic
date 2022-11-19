# Password recovery tool

## Attack tree

```text
1 Passwords
    1.1 Download password recovery tool such as LazAGne (AND)
    1.2 Set permissions to 777 (direct download URL) (AND)
    1.3 Set up (or start) a webserver (AND)
    1.4 Create gmail account with app password (in Security section)
    1.5 Upload password recovery tool to webserver /var/www/html/evil-files or other from target reachable location (AND)
    1.6 Make a (.bat extension) script that downloads the password recovery tool, execute it and send an email with the result (AND)
    ...
```

## Notes

* LazaGna needs to be executed on target computer and displays logs on screen or stores them in a local file.
* Use a file that downloads LazAgne, execute it and send an email with the result back.

## Tools

* [LaZagnE](https://github.com/0x0ff537/LaZagne/)
* [LAzAgne wiki](https://github.com/AlessandroZ/LaZagne/wiki)
* [Compile Lazagne](https://github.com/AlessandroZ/LaZagne/wiki/How-to-compile) (because the releases are detectable)
* [Powershell scripting](https://docs.microsoft.com/en-us/powershell/scripting/samples/sample-scripts-for-administration?view=powershell-7.2)