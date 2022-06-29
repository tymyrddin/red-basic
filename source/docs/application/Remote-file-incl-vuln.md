# Shell from remote file inclusion vulnerabilities

## Attack tree

```text
1 Inject code in remote server
    1.1 Create payload (use other extension to prevent local server from executing it)
    1.2 Start listener on hacking machine
    1.3 Add url of payload location to url of the target server
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

Using remote file inclusion (RFI), an adversary can cause a web application to include a remote file. 
This is possible for web applications that dynamically include external files or scripts. Potential web security 
consequences of a successful RFI attack range from sensitive information disclosure and 
[Cross-site Scripting (XSS)](XSS.md) to [remote code execution](Remote-code-execution.md) and, as a final result, 
full system compromise.

If PHP is configured to `allow_url_fopen` and `allow_url_include` (in `etc/php5/cgi/php.ini`), then the
[Local inclusion file attack](Local-file-incl-vuln.md) can be used as a remote file inclusion attack.

If playing with metasploitable2, set these two to `On` and restart apache2: `sudo /etc/init.d/apache2 restart`

## Tools
* [Burp suite CE proxy](https://portswigger.net/burp/documentation/desktop/getting-started/intercepting-http-traffic)

## Cheatsheets
* [Remote file inclusion](https://tymyrddin.github.io/cheatsheets/docs/application/rfi.html)
* [Reverse shell commands](https://tymyrddin.github.io/cheatsheets/docs/application/reverse-shell-commands.html)
* [Path Traversal Cheat Sheet: Windows](https://www.akimbocore.com/article/windows-path-traversal-cheat-sheet/)
* [Path Traversal Cheat Sheet: Linux](https://www.akimbocore.com/article/linux-path-traversal-cheat-sheet/)

## Mitigations
* [Remote file inclusion](https://tymyrddin.github.io/app-mitigations/docs/coding/Local-file-inclusion.html)