# Webpage with BeEF hook

## Attack tree

```text
1 Test (AND)
    1.1 Create index.html with basic beef hook in /var/www/html/ (AND)
    1.2 Add basic beef hook script to it (AND)
    1.3 Start apache2 server (AND)
    1.4 Start beef (AND)
    1.5 Go to URL with target machine (AND)
    1.6 Watch IP address and info appear in beef (AND)
2 Inject hook in a page (AND)
    2.1 Download site with webscrapbook (AND)
    2.2 Extract downloaded archive and rename for easier use (AND)
    2.3 Open a page (like index.html) (AND)
    2.4 Add BeEF hook in <head> tag (AND)
    2.5 Copy all code to apache2 webroot
3 Manipulate URL (AND)
    3.1 Shorten
    3.2 QR code
    3.3 Obfuscate
4 Deliver link to target
```

## Notes 

Just for testing.

## Tools

* [BeEF in Kali](https://www.kali.org/tools/beef-xss/)
* [WebScrapBook](https://addons.mozilla.org/en-GB/firefox/addon/webscrapbook/)
* [Domain obfuscator](https://splitline.github.io/domain-obfuscator/)