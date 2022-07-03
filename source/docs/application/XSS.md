# Cross-site scripting (XSS)

## Attack tree

```text
1 Cross-site scripting (XSS)
    1.1 Stored and reflected: Persistent/stored XSS (OR)
    1.2 Intermediately reflected: Reflected XSS (OR)
    1.3 Accessed via JS: DOM based XSS
```

## Notes
XSS is a web-based attack performed on vulnerable web applications, the victim is the user and not the application. An XSS attack can redirect to phishing sites or fake login pages, steal the users cookies with which they can gain access to other web applications with authenticated sessions, insert links to remotely hosted client side exploits within a html body, all leading to installing software on the system, such as keyloggers and remote shells.

In order to successfully exploit a XSS vulnerability, find a controllable value which is reflected in the web page.
* Intermediately reflected: If the value of a parameter or even the path is being reflected in the web page, exploit a Reflected XSS.
* Stored and reflected: If a value is saved in the server (page, database) and is reflected every time a page is accessed, exploit a Stored XSS.
* Accessed via JS: If a value is accessed using JS, exploit a DOM XSS.
