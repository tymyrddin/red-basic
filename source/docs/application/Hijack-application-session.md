# Hijack session (application)

A web server needs a method to recognize every user’s connections. The most useful method depends on a token that the Web Server sends to the client browser after a successful client authentication. A session token is composed of a string of variable width and can be used in different ways, like in the URL, in the header of the http requisition as a cookie, in other parts of the header of the http request, or in the body of the http requisition.

## Attack tree

```text
1 Get valid token session (Session ID)
    1.1 Use a sniffer (OR)
    1.2 Use an XSS attack to steal the session token
    1.3 Use (Man in the Middle) MitM
    1.4 Use (Man in the Browser) MitB
2 Use the valid token session to gain unauthorised access to the web server 
```