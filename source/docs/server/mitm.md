# MitM between users and webserver

## Attack tree

```text
1 intercept communications between the end-users and web server(s)
    1.1 Set up a Wi-Fi access point which mimics a real access point nearby (AND)
    1.2 Use a tool such as sslstrip to disable all https redirects and change https:// links to unencrypted http:// links
```

## Mitigations

* Use HTTPS.
* Use preloaded HSTS.
* Harden SSL/TLS ciphers.
  * Implement forward secrecy
  * Use authenticated encryption
  * Disable legacy protocols
  * [Generate a secure SSL configuration](https://ssl-config.mozilla.org/)
