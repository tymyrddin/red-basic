# Cross-site scripting (XSS)

XSS is a web-based attack performed on vulnerable web applications, the victim is the user and not the application. An XSS attack can redirect to phishing sites or fake login pages, steal the users cookies with which they can gain access to other web applications with authenticated sessions, insert links to remotely hosted client side exploits within a html body, all leading to installing software on the system, such as malware, key loggers and remote access tools (RATs).

## Attack

```
1 User logged in site (AND)
2 Locate vulnerability (AND)
    2.1 Search for vulnerability patterns
    2.2 Identify unpatched software
    2.3 Analyse error messages
3 Inject attack script
    3.1 Create attack script (AND)
    3.2 Use web form (OR)
    3.3 Use URL
```