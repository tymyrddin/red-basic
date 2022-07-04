# Veiled backdoor

## Attack tree

```text
1 Create a reverse https payload in Veil (AND)
    1.1 Choose payload and set options (reverse, https, lhost, lport) (AND)
    1.2 Generate (AND)
    1.3 Check it is not detected by AV
2 Set up listener using Metasploit (AND)
    2.1 use exploit/multi/handler (AND)
    2.2 set PAYLOAD (reverse, https, lhost, lport) (AND)
    2.3 exploit
3 Deliver payload (AND)
    3.1 start apache2 on kali (service apache2 start) (AND)
    3.2 put payload in /var/www/html/evil-files (create dir) (AND)
    3.3 Deliver
        3.3.1 Nothing smart, just to test it works - Download from a machine in the network (OR)
        3.3.2 A little smarter, using BeEF - Fake notification bar
4 Post exploitation
```

## Notes

Just a skeleton, smarter ways to deliver in post exploitation.

## Tools

* [Install veil for kali](https://github.com/Veil-Framework/Veil/)
* [NoDistribute](https://nodistribute.com/)
* [Metasploit](https://www.kali.org/docs/tools/starting-metasploit-framework-in-kali/)
* [BeEF XSS](https://www.kali.org/tools/beef-xss/)

## Troubleshooting

* [Veil Installation error Failed to run (wine) Python pip pefile... Exit code: 1](../trouble/Veil.md)

## Cheatsheets

* [Evading Anti-Virus](cheatsheets:docs/stealth/evading-av)
* [Why use meterpreter](https://www.offensive-security.com/metasploit-unleashed/about-meterpreter/#Meterpreter_Design_Goals)