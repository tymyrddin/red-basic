# Man-in-the-Browser (MitB)

## Attack tree

```text
1 User logged in vulnerable web application (AND)
2 Malware (trojan/rootkit) installed as part of the client (browser) (AND)
    2.1 Browser Helper Object (BHO, Internet explorer) (OR)
    2.2 Active-X controls (OR)
    2.3 Browser extension/Add-on/Plugin
3 Send HTTP request
    3.1 Man-in-the-Middle between client (browser) and server
        3.1.1 Hook browser and steal HTTP request (AND)
        3.1.2 Modify and send stolen HTTP request (AND)
        3.1.3 Release hook
```

## Notes

MitB is a proxy Trojan horse that infects a web browser by taking advantage of vulnerabilities in browser security to modify web pages, modify transaction content or insert additional transactions, invisible to both the user and host web application, regardless of security mechanisms such as SSL/PKI and/or two, three or four factor authentication solutions. Neither encryption nor OTP can protect against a MitB. Authentication is for validation of identity credentials, not transaction verification. An effective mitigation could be using an out-of-band (OOB) transaction verification process.


