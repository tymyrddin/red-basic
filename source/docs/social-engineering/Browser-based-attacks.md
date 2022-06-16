# Browser-based attacks

## Attack tree

```text
1 Phishing (OR)
2 Use browser as gateway (OR)
    2.1 Cross-site scripting (XSS): Execute some browser code in the context of a vulnerable web application.
    2.2 Cross-Site Request Forgery (CSRF): Trick the browser into visiting a site or clicking on a link 
    that submits a specially-crafted request to the vulnerable web application.
    2.3 Clickjacking: Design a website that embeds the visitor’s desired web application while floating 
    invisible HTML elements above the web app’s legitimate user interface. The user will believe he is 
    interacting with the legitimate site, while the code intercepts the user input. 
    2.4 Man-in-the-Browser: Design an application that runs directly on the user’s computer and embeds 
    itself into the browser as an add-on or a DLL to intercept and tamper with traffic sent by the browser.
3 Exploit a vulnerability in the browser (OR)
4 Exploit a vulnerability in software invoked by browser
    4.1 Flash
    4.2 Adobe Reader
    4.3 Java Runtime Environment (JRE)
    4.4 Browser add-ons/extensions
    4.5 Other local software that the browser can invoke
```

## Notes

Three web attack vectors are responsible for the majority of computer attacks that involve a web browser. Most browser-based attacks include one or two of these three techniques. Phishing and the gateway techniques are medium and not high risk issues, down to the delivery method of attack and the execution vectors. These vulnerabilities require user interaction and an element of social engineering because for it to succeed users have to voluntarily interact with the malicious pages.
