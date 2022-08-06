# Mail delivery

## Attack tree

```text
1 Spoof email using mailserver and sendemail on Kali (OR)
    1.1 Sign up for a mailserver (AND)
        1.1.1 Paid email marketing service (OR)
        1.1.2 Paid service with a free plan
    1.2 Use sendemail
        1.2.1 Specify username (-xu) and password (-xp) with the SMTP settings in configuration mailserver (AND)
        1.2.2 Specify server and port (-s) with the SMTP settings in configuration mailserver (AND)
        1.2.3 Set from email address (-f) (AND)
        1.2.4 Set to email address (-t) (AND)
        1.2.5 Set subject (-u) (AND)
        1.2.6 And body (-m) (AND)
        1.2.7 Use the advanced option (-o) for specifying the "From: Name <email address>" message-header
2 Spoof email using php mail() function on hosting
    2.1 Sign up for a free hosting plan (AND)
        2.1.1 Choose domain later (AND)
        2.1.2 Email and other things not needed either
    2.2 Use php mail() function
        2.2.1 Go to the file manager of the website and public_html or name of website (different on each provider): find it empty or nearly empty (AND)
        2.2.2 Create the send.php file and rename it to .txt for upload (AND)
        2.2.3 Upload and change back extension to .php (AND)
        2.2.4 Bring up the form and enter to, from, name, subject, message (AND)
        2.2.5 Send (AND)
        2.2.6 Remove send.php from server
```
## Notes

* Use [reconnaissance information](../reconnaissance/Info-person.md) for the from and to
* Use what you discovered about them and their interests, for the subject and body
* Have the body contain a link to a downloadable, for example in Dropbox (changing the link values to make it a direct download)

## Tools

* [sendemail](https://www.kali.org/tools/sendemail/)
* [SMTP diagnostics](https://mxtoolbox.com/diagnostic.aspx)

## Mitigations

* [Windows PC operations security](windows-pc-mitigations:docs/opsec/README)
* [macOS operations security](macos-mitigations:docs/opsec/README)
* [Linux PC operations security](linux-pc-mitigations:docs/opsec/README)