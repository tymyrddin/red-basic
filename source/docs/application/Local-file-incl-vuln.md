# Shell from local file inclusion vulnerabilities

## Attack tree

```text
1 Inject code in environment files
    1.1 Intercept request to read the environment file (Burp proxy or similar)
    1.2 Start listener on hacking machine
    1.3 Modify request (for example change user-agent value to reverse shell code)
    1.4 Send commands
2 Using log files (for example /var/logs/auth.log)
    2.1 Check a login attempt gets logged
    2.2 Start listener on hacking machine
    2.2 ssh "<?passthru(base64_decode('base64 encoding of reverse shell code'));?>"@IP-address-server
    2.3 Enter whatever password (not important)
    2.4 Reload browser /var/logs/auth.log page
    2.4 Send commands
```

## Notes

Local File Inclusion (LFI) means that through some way someone may be able to access files on the local system 
through the application. LFI is particularly common in php-sites.

A local file inclusion attack allows adversaries to read files on the server that is running a web application. 
These files may include the application's source code and data, credentials for backend systems, or sensitive OS files. 
The attacker may even be able to write to arbitrary files on the server, modifying the application's data or behaviour, 
or to even take full control of the server.

All an attacker needs to perform a file inclusion attack is a web browser, a proxy to intercept and modify requests and 
some knowledge on where to find default files and directories on the system.

## Tools
* [Burp suite CE proxy](https://portswigger.net/burp/documentation/desktop/getting-started/intercepting-http-traffic)

## Cheatsheets
* [Local file inclusion](https://tymyrddin.github.io/cheatsheets/docs/application/lfi.html)
* [Reverse shell commands](https://tymyrddin.github.io/cheatsheets/docs/application/reverse-shell-commands.html)
* [Path Traversal Cheat Sheet: Windows](https://www.akimbocore.com/article/windows-path-traversal-cheat-sheet/)
* [Path Traversal Cheat Sheet: Linux](https://www.akimbocore.com/article/linux-path-traversal-cheat-sheet/)

## Mitigations
* [Local file inclusion](https://tymyrddin.github.io/app-mitigations/docs/coding/Local-file-inclusion.html)