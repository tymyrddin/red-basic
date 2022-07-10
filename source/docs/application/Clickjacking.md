# Clickjacking

## Attack tree

```text
1 User logged in vulnerable web application (AND)
2 Send request to site
    2.1 Create valid request 
        2.1.1 Analyse real requests of the site (AND)
        2.1.2 Embed a page from a vulnerable web application, as a hidden or transparent iframe in 
        a page designed to motivate the user to click on a location (button, link)
```

## Notes

In its simplest form, clickjacking is attacking users’ interactive “clicks” via transparent or concealed layers. 
These layers can be placed over likely attack vectors such as buttons and hyperlinks, potentially deceiving users into 
interacting with an adversaries' code. The transparent iframe (from the vulnerable application) is overlaid on top of 
the attacker’s page such that when a user clicks on it, she clicks on an element of the transparent iframe, instead of 
on the visible button or link. If the user already has an active authenticated session with the vulnerable application, 
this click can initiate an unintended transaction with the vulnerable application.

This vulnerability exists when the vulnerable application allows critical pages to be embedded as iframes within 
unrelated pages, and when requests to get these critical pages are open to Cross-Site Request Forgery (CSRF). This 
combination of attacks allows retrieval and misuse of pages to stage an undesirable transaction that needs a final 
click by an authenticated (logged in) user (for example, a funds transfer).

