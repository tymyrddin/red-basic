# Enumerate webserver directories

```text
1 Enumerate web server directories to extract info about web functionalities, login forms, scripts, etc. (AND)
2 Directory traversal
    2.1 Search for sensitive default script and file directories (AND)
    2.2 If script, try execute the found command
```

## Notes

* `http-enum.nse` offers a quite extensive fingerprint, especially when including Nikto database, but no guarantees all will be seen. 
* Also try [directory traversal](../server/traversal.md).

## Tools

* [Nmap](https://nmap.org)
* [http-enum.nse](https://nmap.org/nsedoc/scripts/http-enum.html)
* [FDSploit](https://github.com/chrispetrou/FDsploit)