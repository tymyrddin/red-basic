# HTTPS spoofing

## Attack tree

```text
1 Homograph attack
    1.1 Register a domain name that is similar (using punycode for example) to the domain name of the target website (AND)
    1.2 Register its SSL certificate to make it look legitimate and secure
2 Social engineering
```

## Notes

* A forged certificate is sent to the target’s browser after the initial connection request to a secure site is made. It contains a digital thumbprint associated with the compromised application, which the browser verifies according to an existing list of trusted sites and because most browsers support the display of punycode hostnames in their address bar, it allows the adversary to access data entered by the victim before it is passed to the application. The browser shows that the website’s certificate is legitimate and secure, and users will not notice that it is a bogus version of the site they expect to visit.
* In HTTPS session spoofing an adversary uses stolen or counterfeit session tokens to initiate a new session and impersonate the original user, who might not be aware of the attack. The difference between [HTTPS session hijacking](../network/SSL-hijacking.md) and spoofing lies in the timing of the attack. Session hijacking is done against a user who is logged in and authenticated, so from the target's point of view the attack will most likely cause the application to behave unpredictably or crash.
 
## Articles

* [Phishing with Unicode Domains](https://www.xudongz.com/blog/2017/idn-phishing/), Xudong Zheng, April 14, 2017
