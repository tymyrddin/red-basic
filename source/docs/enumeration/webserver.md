# Enumerate webserver directories

```text
1 Enumerate web server directories to extract info about web functionalities, login forms, scripts, etc.
2 Try a directory traversal
    2.1 Search for sensitive default script directories (AND)
    2.2 Try execute the found command
```

## Notes

`http-enum.nse` offers a quite extensive fingerprint, especially when including Nikto database, but no guarantees all will be seen. So also try a traversal.

## Tools

* [Nmap](https://nmap.org)
* [http-enum.nse](https://nmap.org/nsedoc/scripts/http-enum.html)
* [FDSploit](https://github.com/chrispetrou/FDsploit)