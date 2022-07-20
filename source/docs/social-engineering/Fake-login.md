# Steal login information with fake login page

## Attack tree

```text
1 Clone login page with for example, webscrapbook (AND)
    1.1 Download login page -> capure tab (source) (AND)
    1.2 Extract downloaded archive and rename for easier use
2 Use set on Kali (AND)
    2.1 Social Engineering Attacks (1) -> Website Attack vectors (2) -> Credential Harvester Attack method (3) -> Custom Import (3) (AND)
    2.2 Enter IP address, absolute path to extracted clone (ending with /) (AND)
    2.3 Copy entire folder (2) (AND)
    2.4 URL for the original website
3 Manipulate URL (AND)
    3.1 Shorten
4 Deliver link to target (spoof email from support to get user to login)
```

## Notes

The simplest scenario. Explore and get creative.

## Tools

* [WebScrapBook](https://addons.mozilla.org/en-GB/firefox/addon/webscrapbook/)
* [Social engineering toolkit](https://www.kali.org/tools/set/)