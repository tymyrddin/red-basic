# Poison cache

## Attack tree

```text
1 Identify and evaluate unkeyed inputs (AND)
2 Obtain a harmful response from the back-end server (AND)
3 Get the response cached
```

## Notes

* When testing for unkeyed inputs on a live website, use cache buster (to make the response not be served to others).
* If an input is reflected in the response from the server (unsanitized), or used to dynamically generate other data, 
it could be an entry point for web cache poisoning. 
* Play around to discover how to get a response cached. 

## Tools

* [Param Miner](https://portswigger.net/bappstore/17d2949a985c4b7ca092728dba871943)

## Articles

* [Practical Web Cache Poisoning](https://portswigger.net/research/practical-web-cache-poisoning), Portswigger
* [Web Cache Entanglement: Novel Pathways to Poisoning](https://portswigger.net/research/web-cache-entanglement), Portswigger

## Mitigations

Web cache poisoning vulnerabilities arise due to general flaws in the design of caches and/or its implementation in an application.

* Turn it off
* Restrict caching to purely static responses