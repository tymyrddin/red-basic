# Modifying code to bypass AV

## Attack tree

```text
1 Use a different payload (OR)
2 Change payload settings (OR)
3 Change code
    3.1 Modify source code (OR)
        3.1.1 It is not the shellcode itself (AND)
        3.1.2 Playing with the params and formats 
    3.2 Modify compiled code in hex editor
        3.2.1 Replacing ascii code with exactly the same amout of characters
4 Customise payload code using existing templates
5 Make payloads from scratch
```

## Notes

Whether delivering a payload through an application vulnerability exploit, or through social engineering, running code 
on target machines is part of most penetration testing. That means bypassing antivirus software or other host-based 
protections.

AV programs use database of signatures to detect malware. Modifying backdoor code will change its signature.

* Open backdoor with text editor.
* Make sure shellcode is not detected, if it is then change payload settings or use a different one.
* Remove all arguments, add them one by one to identify the one triggering AV programs
* Remove/modify detectable code.
* Test whether still detected

Some parts of the code may be doing nothing:

* Open file with hex editor.
* Change values that don’t affect code execution.
* Make small changes and save and test the file whether still executes.
* Test whether still detected.

Note that creating a new payload or shellcode that creates a new signature that is not present in the antivirus' tools 
database can still be effective but falls short on the new solutions that base their detection on heuristics 
and behavioural analysis. Learn to write your own payloads using existing templates for example, or from scratch in
python, in which case: Keep it as simple and native as possible.

## Examples
### Customise payload code using templates

For customisation, use Metasploit templates in the `data/templates/src` directory for DLLs, EXEs, and Windows Services.
Plug in [exploit-db shellcodes](https://www.exploit-db.com/shellcodes) into the template. Or use `msfpayload` or 
`msfvenom` from Metasploit to generate C shell code to, for example, bind a shell to TCP port 4444 and plug that into 
the template:
	
	$ ./msfpayload windows/shell_bind_tcp C

After compilation, check to see if the AV products running in the lab detect the bugger. If it gets detected start 
playing with segments and other formats, etcetera.

## Tools

* [NoDistribute](https://nodistribute.com/)
* [AntiScan](https://antiscan.me/)
* [KleenScan.com](https://kleenscan.com)

## Developments

* [Independent Tests of Anti-Virus Software](https://www.av-comparatives.org/)
* [AV Test](https://www.av-test.org/en/)
