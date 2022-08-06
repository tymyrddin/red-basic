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

* Turn caching off (OR)
* If you *have* to use it (big site, many visitors)
  * Understand and restrict where caching is done. Cache static response, such as `.js`, `.css`, `.png` files, blog posts, or any page that is always identical. Make sure that an adversary can not trick the back-end server into retrieving their malicious version of a static resource.
  * Disable all headers which are not necessary for the website's functionality. Especially the Host header. Double-check whether which urls really need to be absolute. Instead use relative urls.
  * Do not exclude something from the cache key, rewrite the request. Avoid using user inputs (HTTP Headers) to be used as the cache key.
  * Do not accept fat GET requests. 
  * Some third-party technologies permit such fat GET requests by default. In general, disable caching by third party frameworks. Do caching at one point.
  * Patch client-side XSS vulnerabilities. Including those that seem not exploitable. They can become exploitable due to strange behaviours of the cache, so that even in the event of such a vulnerability, the user’s browser can’t be exploited.