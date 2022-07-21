# On steroids: SEO poisoning

From research, what appears to be happening: The below search engine poisoning attack tree can be used for feature extraction.

## Attack tree

```text
1 Set up branching logic (usually PHP script) (AND)
    1.1 Identify crawlers (OR)
        1.1.1 Query IP of page request ($_SERVER['REMOTE_ADDR']) and compare against usual 
        search engine IP ranges) (OR)
        1.1.2 Check user-agent string ($_SERVER['HTTP_USER_AGENT']) to flag requests from 
        crawlers that use identifying strings
    1.2 Identify users 
        1.2.1 Check referrer ($_SERVER['HTTP_REFERER']) against a list of strings used by 
        search engines (OR)
        1.2.2 Check the referrer URL for multiple occurrences of & (field value pair delimiters)
2 Get and select keywords and topical phrases (AND)
    2.1 Fetch and select latest keywords from
        2.1.1 C&C server (less resilient) (OR)
        2.1.2 Google Trends (OR)
        2.1.3 Other sources
    2.2 Optional: Log information about page requests received to monitor requests (for 
    fine-tuning and improvements)
        2.2.1 Keywords user arrived by
        2.2.2 Timestamp
        2.2.3 User agent string
        2.2.4 Referrer string
        2.2.5 IP from which page request is received
    2.3 Download search engine results (AND)
        2.3.1 PHP client URL library (OR)
        2.3.2 cURL (OR)
        2.3.3 fsockopen()
    2.4 Extract meta content from the downloaded pages (using regular expressions) (AND)
    2.5 Optional: Boost page ranking
        2.5.1 Get links of other SEO pages
            2.5.1.1 Same server
            2.5.1.2 Related servers 
        2.5.2 Intersperse extracted meta content with links to other SEO pages, random time/dates, 
        images, video content
3 Page generation (AND)
    3.1 Same page for crawlers and users (OR)
        3.1.1 Generate page
        3.1.2 Redirect
            3.1.2.1 Redirect by active content embedded in page (OR)
            3.1.2.2 Only load additional active content in page if request is from a user 
                3.1.2.2.1 JavaScript (OR)
                3.1.2.2.2 ActionScript in embedded Flash (navigateToURL( new URLRequest("*yourpage*"), "_self");) (OR)
                3.1.2.2.3 Another way of redirecting using active content 
    3.2 Different pages for user and crawler
        3.2.1 Generate SEO page for crawlers (AND)
            3.2.1.1 Static HTML (OR)
            3.2.1.2 Dynamic generation (OR)
            3.2.1.3 SEO related sub-domains
        3.2.2 Redirect users (a few times)
            3.2.2.1 Server-side scripting with PHP header() (OR)
            3.2.2.2 Apache HTTP Server mod_alias
            3.2.2.3 Apache HTTP Server mod_rewrite (redirecting requests to a canonical domain name) (OR)
            3.2.2.4 Nginx rewrite (OR)
            3.2.2.5 Refresh Meta tag in document (add anchor in the “body” section for users whose browsers do not support this feature) (OR)
            3.2.2.6 HTTP refresh header in a perl or python script (OR)
            3.2.2.7 JavaScript (OR)
            3.2.2.8 Another way of redirecting
4 Landing page
    4.1 Adult and pornographic websites (OR)
    4.2 Internet services sites (advertising campaign) (OR)
    4.3 Politics and religion (on a mission) (OR)
    4.4 Exploit servers 
        4.4.1 Redirection chain to a final landing page with malware payloads
        4.4.2 Redirection to a MaaS (Malware-as-a-Service) platform which starts a redirection 
        chain leading to final landing page
```

## Notes


The phrase search engine optimization poisoning (SEO poisoning) is in use to describe one of two types of activities:

* Black hat SEO techniques used to achieve high search engine ranking, usually (but not only) to attack visitors. The techniques often involve content spamming, (all sorts of) link spamming, cloaking, doorway pages and redirection. These attacks often follow trending search terms. For example during natural disasters, when attackers attempt to have victims send monetary aid to fake accounts or during major political campaigns and other major world events. If its intent is malicious, the attacker aims to install malware such as trojans, attack the user’s machine, or trick the user into providing sensitive data (see attack tree).
* Exploiting typical web vulnerabilities on existing high-ranking web pages and using them to spread malware. If, for example, a high-ranking web page has a stored XSS vulnerability, the code may either directly attempt to spread malware or redirect the user to a different site (using redirection like used in black hat SEO).

Any search engine software can expect the same search fraud problem as on the internet with similar impacts.

* Spam web pages will need to be weeded out from the index.
* Combating spam is intertwined with search engine poisoning as that attack uses SEO fraud techniques.

## Cheatsheets

* [Redirecting](cheatsheets:docs/payloads/redirecting)
