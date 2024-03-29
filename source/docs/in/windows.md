# Windows malware

## Attack tree

```text
1 Create backdoor (AND)
    1.1 Metasploit meterpreter (https payload) (OR)      
        1.1.1 With Veil/Evasion
            1.1.1.1 Choose payload and set options (reverse, https, lhost, lport) (AND)
            1.1.1.2 Generate (AND)
        1.1.2 Check it is not detected by AV
        1.1.3 Start listener using Metasploit (AND)
            1.1.3.1 Use exploit/multi/handler (AND)
            1.1.3.2 Set PAYLOAD (reverse, https, lhost, lport) (AND)
            1.1.3.3 Exploit
    1.2 Powershell stager (http payload)
        1.2.1 Powershell-empire server (AND)
        1.2.2 Powershell-empire client (AND)
            1.2.2.1 Create listener (uselistener http) and set Port (AND)
            1.2.2.3 Execute (or Generate) (AND)
            1.2.2.3 Create stager (usestager windows/launcher_bat) and set Listener to just created listener (AND)
            1.2.2.4 Execute (or Generate)
        1.2.3 Check it is not detected by AV
2 Deliver payload (start server) (AND)
    2.1 start apache2 on kali (service apache2 start) (AND)
    2.2 put payload in /var/www/html/evil-files (create dir) (AND)
    2.3 Deliver
        2.3.1 Nothing smart, just to test it works - Download from a machine in the network (OR)
        2.3.2 A little smarter, using BeEF - Fake notification bar
        2.3.3 ...
3 Post exploitation
```

## Notes

### Veil
* Veil is a framework for generating Undetectable backdoors. Make that less detectable.

### FatRat

Also attempts to generate Undetectable Metasploit backdoors for Windows, macOS, Linux, and Android. FatRat uses encryption to bypass most of the Antivirus. It can be configured for system exploitation, post-exploitation 
attacks, browser attacks, DLL attacks, FUD payloads, etc.

* SearchSploit gives a list of payloads and backdoors for every type of target
* File Pumper increases size of a payload to increase stealth

## Tools

* [Install Veil 3 for kali](https://github.com/Veil-Framework/Veil/)
* [GitHub TheFatRat](https://github.com/Exploit-install/TheFatRat)
* [Empire on Kali](https://www.kali.org/tools/powershell-empire/)
* [Github Empire 4](https://github.com/BC-SECURITY/Empire)
* [Metasploit](https://www.kali.org/docs/tools/starting-metasploit-framework-in-kali/)
* [BeEF XSS](https://www.kali.org/tools/beef-xss/)

## Resources

* [Empire wiki](https://bc-security.gitbook.io/empire-wiki/)
* [Why use meterpreter](https://www.offensive-security.com/metasploit-unleashed/about-meterpreter/#Meterpreter_Design_Goals)
