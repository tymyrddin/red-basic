# Steal access info with fake login page

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
4 Deliver link to target (for example spoof email from support to get user to login)
5 Wait for it ...
```

## Example using SET

### Set up a clone

1. On Kali, run `ifconfig` in a terminal and record the IP address.
2. In the terminal session, run the `setoolkit` command to launch SET.
3. Read and then choose `y` to agree to the terms to go to the SET main menu screen.
4. Type `1` to perform a social engineering attack and press Enter.
5. Type `2` for Website Attack Vectors and press Enter.
6. Type `3` to perform a credential harvester attack and then press Enter.
7. Type `2` to choose Site Cloner and press Enter. Site Cloner copies a real website in order to create a fake site that
tricks users into entering their passwords.
8. You are asked for the IP address for the POST back in Harvester/Tabnabbing. This is the IP address of where you want the site to be
copied. Type the IP address of your Kali Linux and press Enter.
9. You are asked which website to clone. Clone the Facebook website with `https://www.facebook.com`. The Facebook site is copied to your Kali system and set up to listen on port 80.
10. To test the site out, launch a web browser and type `http://<IP_of_Kali>`.

### Trick victim(s) into visiting the fake site

11. With SET running, have users navigate to the fake website and log on. Send an email or text message with the link.

### Check the harvester file for passwords

12. Switch back to the terminal running SET. Some activity was generated in SET.
13. Press CTRL+C to generate a report. The reports are stored in the `/root/.set//reports` folder. There is an HTML 
and an XML report. To check out the HTML report, click the folder icon in the Kali toolbar and then choose Home on the 
left.
14. Set "Show Hidden Files" and navigate to `.set/Reports`.
15. Double-click the HTML report to view the results including any email addresses and passwords typed into the fake 
site.

## Notes

The simplest scenario. It is not necessary to use SET for the cloning. Other tools like WebScrapBook and curl can do 
too. Explore and get creative.

## Tools

* [WebScrapBook](https://addons.mozilla.org/en-GB/firefox/addon/webscrapbook/)
* [Social engineering toolkit](https://www.kali.org/tools/set/)