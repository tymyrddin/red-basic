# Shell from remote file inclusion vulnerabilities

## Attack tree

```text
1 Inject code in remote server
    1.1 Create payload (use other extension to prevent local server from executing it)
    1.2 Start listener on hacking machine
    1.3 Add url of payload location to url of the target server
    1.4 Send commands
```

## Notes

Using remote file inclusion (RFI), an adversary can cause a web application to include a remote file. 
This is possible for web applications that dynamically include external files or scripts. Potential web security 
consequences of a successful RFI attack range from sensitive information disclosure and 
[Cross-site Scripting (XSS)](XSS.md) to [remote code execution](Remote-code-execution.md) and, as a final result, 
full system compromise.

If PHP is configured to `allow_url_fopen` and `allow_url_include` (in `etc/php5/cgi/php.ini`), then the
[Local inclusion file attack](Local-file-inclusion.md) can be used as a remote file inclusion attack.

If playing with metasploitable2, set these two to `On` and restart apache2: `sudo /etc/init.d/apache2 restart`

## Cheatsheets
* [Remote file inclusion](cheatsheets:docs/application/rfi)
* [Reverse shell commands](cheatsheets:docs/application/reverse-shell-commands)
* [Path Traversal Cheat Sheet: Windows](https://www.akimbocore.com/article/windows-path-traversal-cheat-sheet/)
* [Path Traversal Cheat Sheet: Linux](https://www.akimbocore.com/article/linux-path-traversal-cheat-sheet/)

## Mitigations
* [Remote file inclusion](app-mitigations:docs/coding/lfi)