# Cross-Site Request Forgery (CSRF)

## Attack

```
1 User logged in site (AND)
2 Send request to site
    2.1 Create valid request
        2.1.1 Analyse real requests of the site (AND)
        2.1.2 Use XSS to get session token in use by site (OR)
        2.1.3 Create a request forging the HTTP Referrer attribute
            2.1.3.1 Analyse real requests of the site (AND)
            2.1.3.2 Forge HTTP request with Flash (OR)
            2.1.3.3 Forge HTTP request with XMLHTTPRequest 
```

