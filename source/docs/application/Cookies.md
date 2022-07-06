# Become admin by manipulating cookies

## Attack tree

```text
1 Logging in as admin without password 
    1.1 Using a cookie editor (OR)
        1.1.1 Find UID cookie
        1.1.2 Change value (likely UID 1 will work)
        1.1.3 Send
    1.2 Using JSON Web Tokens (JWT)
        1.2.1 Find and copy access_token of any user
        1.2.2 Decode the three parts of the JWT to understand its structure
        1.2.3 Change values (for example {"alg":null}, iat value, admin to be true ...)
        1.2.4 Encode the two parts (leave out the ==, connect parts with fullstop .)
        1.2.5 Pause 
        1.2.6 Post in access_token (before JSESSION) and connect parts with fullstop .
        1.2.7 Resend and check Response
```

## Notes

* Logging in as admin without password by using a cookie editor only works if no session ID or token is used.
* If the cookie is using some Base encoding (like Base64) or similar it may be possible to decode it, change the content and impersonate arbitrary users.

## Tools

* [Cookie Quick Manager](https://addons.mozilla.org/en-US/firefox/addon/cookie-quick-manager/)
* [Developer tools: Storage inspector](https://firefox-source-docs.mozilla.org/devtools-user/storage_inspector/index.html)
* [Burp suite CE proxy](https://portswigger.net/burp/documentation/desktop/getting-started/intercepting-http-traffic)
* [Base64 encode and decode](https://www.base64decode.org/) OR use tab in Burp suite

## Articles

* [JWT](https://jwt.io/introduction)
