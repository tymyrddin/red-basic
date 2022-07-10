# Browser-based attacks

## Attack tree

```text
1 Phishing (OR)
2 Use browser as gateway (OR)
    2.1 Cross-site scripting (XSS)
    2.2 Cross-Site Request Forgery (CSRF)
    2.3 Clickjacking 
    2.4 Man-in-the-Browser
3 Exploit a vulnerability in the browser (OR)
4 Exploit a vulnerability in software invoked by browser
    4.1 Adobe Reader
    4.2 Java Runtime Environment (JRE)
    4.3 Browser add-ons/extensions
    4.4 Other local software that the browser can invoke
```

## Notes

Three web attack vectors are responsible for the majority of computer attacks that involve a web browser. Most browser-based attacks include one or two of these three techniques. Phishing and the gateway techniques are medium and not high risk issues, down to the delivery method of attack and the execution vectors. These vulnerabilities require user interaction and an element of social engineering because for it to succeed users have to voluntarily interact with the malicious pages.
