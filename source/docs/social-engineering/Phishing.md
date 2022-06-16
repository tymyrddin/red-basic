# Phishing

## Attack tree

```text
1 Make fake website
    1.1 Clone website (AND)
        1.1.1 Use a tool like cURL or Invoke-WebRequest (powershell)
    1.2 Add payload (AND)
        1.2.1 Change login page to a credential stealing script (OR)
        1.2.2 Implant a malware (Crypted and packed)
    1.3 Upload the phishing kit
2 Gather information on potential victims
    2.1 Consult public databases (OR)
    2.2 Scour social networking sites (OR)
    2.3 Use Sleuthing/(Digital) dumpster diving
2 Use social engineering to persuade a person to go to the phishing site 
```

## Notes

An adversary poses as a legitimate and trusted business using a similar look and feel to regular email notifications to trick users into clicking on a link that takes them a phony website or access portal designed to look like the legitimate company website. Victims are then prompted to enter personal information ranging from login names and passwords to social security numbers, birthdates, account numbers, and other highly sensitive data. Email phishing is popular because of the easy access to databases containing millions of active email addresses, providing potential victims with relatively little risk and almost no cost.

In so-called spear phishing an adversary creates an email message that appears to be from a trusted sender, the tone of the email way more informal than in a phishing attack, and usually contains some sort of emergency with a request for help, in such a way that a quick, instinctive action is required to help the other (before thinking can intervene). With personal information shared on social networking sites (first and last name, names of family members, and employers), spear-phishing is easier than ever.

Whaling is phishing for executives. The victim is researched more thoroughly with reconnaissance and lured with a fake document from, for example, the tax office, and state that the opening of the document requires the installation of some “security software”, or something similar.
