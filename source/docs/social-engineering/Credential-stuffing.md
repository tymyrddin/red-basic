# Credential stuffing

## Attack tree

```text
1 Use a credential stuffing tool such as Sentry MBA (OR)
    1.1 Configure tool (AND)
        1.1.1 The url for the website's login page
        1.1.2 Field markers to help navigate form elements
        1.1.3 Rules for valid password constructions 
    1.2 Optimise and test the attack setup against the live target website (AND)
    1.3 Add combo file (list of usernames and passwords that were valid on another website/application) (AND)
    1.4 Add proxy file (AND)
    1.5 Commence attack 
2 DIY
    2.1 Buy breached credentials (private sales, hacking forums, dark web marketplaces, password dump sites)
    2.2 Check credentials (social media sites, online marketplaces)
        2.2.1 Use botnet (AND)
            2.2.1.1 Create botnet (OR)
            2.2.1.2 Hire botnet
        2.2.2 Stuff credentials against target sites/applications
            2.2.2.1 Bypass security and fraud detection such as IP blacklists or rate limiting (AND)
            2.2.2.2 Spoof the “referer” header value for bypassing referrer checks (AND)
            2.2.2.3 Simulate user with OCR and/or database with possible CAPTCHA images and answers.
            2.2.2.3 Try logins with breached credentials 
```

## Notes


Credential stuffing is currently one of the most common techniques used to take-over user accounts. Credential spilling is when credentials gained from data breaches are sold to other adversaries. Credential stuffing is the large scale use of automated means to test stolen passwords against other unrelated websites. This is a possible and often successful attack because of the tendency for users to recycle their passwords for multiple accounts.

Adversaries no longer need advanced technical skills, specialized equipment, or insider knowledge to successfully attack major websites. Tools are available that bypass traditional security controls, like IP rate limits, reputation lists, blacklists, and other forms of IP-based analysis. CAPTCHA and other controls designed to impede automated interaction with user interfaces are bypassed with Optical Character Recognition (OCR) software and other complementary mechanisms to read and solve those challenges the way that a human user would. A number of forums offer a wide variety of working configurations for various websites for the tools.

Successful logins (usually 0.1-0.2%) allow the adversary to drain the associated accounts of stored values, credit card numbers, and other personally identifiable information and/or to use the account for impersonation, and for actions like sending spam.

