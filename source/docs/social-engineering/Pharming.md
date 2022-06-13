# Pharming

In a phishing attack, an adversary will try to trick a user into visiting a fake website, but anyone can notice that the URL is not the original URL for the website. In a pharming attack (“farming” and “phishing”) website traffic is also redirected to a bogus site, but in contrast to phishing, the URL looks completely legitimate and users easily believe they are at a familiar site. There are two ways to easily achieve this:

* By changing the hosts file (/etc/hosts on Linux and %SystemRoot%\system32\drivers\etc\hosts on Windows) on a target computer. Common ways to replace a host file are creating a self-extracting archive (SFX), a computer application which contains a file archive and the programming to extract this information, or creating a batch file, a text file containing a series of commands to be executed by the command interpreter in windows operating systems.
* By exploitation of a vulnerability in DNS server software. DNS cache poisoning is very difficult to detect. It can last until the TTL, or time to live, expires on the cached data or an administrator realises what has happened and resolves the problem.

In either case, the browser resolves the address of the domain automatically so there is no intervention of any kind on the part of the users and, since nothing unusual has happened, there is no reason to be suspicious.

## Attack:

```
1 Make fake website (AND)
    1.1 Clone website (AND)
        1.1.1 Use a tool like cURL or Invoke-WebRequest (powershell)
    1.2 Add payload (AND)
        1.2.1 Change login page to a credential stealing script (OR)
        1.2.2 Implant a malware (Crypted and packed)
    1.3 Upload the phishing kit
2 Poison DNS cache (if it is a major DNS server, it can poison the caches of DNS servers maintained by 
internet service providers) (AND)
3 Compromise a host and change host file on it to redirect traffic
    3.1 Make replacement (AND)
        3.1.1 Use a self-extracting archive (SFX) (OR)
        3.1.2 Use a batch file
    3.2 Get a user to run it
        3.2.1 Email
        3.2.2 Fake website
        3.2.3 Other social engineering
```

