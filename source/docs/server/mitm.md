# MitM between users and webserver

## Attack tree

```text
1 intercept communications between the end-users and web server(s)
    1.1 Set up a Wi-Fi access point which mimics a real access point nearby (AND)
    1.2 Use a tool such as sslstrip to disable all https redirects and change https:// links to unencrypted http:// links
```

## Mitigations

* [Use TLS/SSL more securely](app-mitigations:docs/protocols/tls-ssl)
