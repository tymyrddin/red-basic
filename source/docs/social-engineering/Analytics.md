# Use analytics to lure a target

## Attack tree

```text
1 Get TrackingID of page (Copy code after YT or YA) (AND)
2 Use set on Kali
    2.1 Social Engineering Attacks (1) -> Third party modules (11) -> Google Analytics attack (2) (AND)
    2.2 manual
        2.2.1 Enter TrackingID UA+Copied code (AND)
        2.2.2 Hostname of target (for example https://youtube.com/) (AND)
        2.2.3 Page (what comes after hostname) (AND)
        2.2.4 Page Title (for example Youtube) (AND)
        2.2.5 Referral page: A by us BeEF hook injected website (AND)
        2.2.6 Send payload on loop (every 60 seconds, so as not to wake up the dogs)
```

## Notes

Target sees a lot of traffic coming from the BeEF injected page and may go and see what's up with that.

## Articles

* [Google Analytics Usage Statistics](https://trends.builtwith.com/analytics/Google-Analytics)
* [Historical trends in the usage statistics of traffic analysis tools for websites](https://w3techs.com/technologies/history_overview/traffic_analysis/all)