# Fake prompts everywhere

## Attack tree

```text
1 Delivery with BeEF
    1.1 BeEF hooked target browser (AND)
    1.2 Pretty theft command in BeEF (OR)
    1.3 Fake Windows 10 Firefox update (OR)
        1.3.1 Windows trojan with firefox installer and Empire backdoor (.exe) (AND)
        1.3.2 BeEF social engineering Clippy command executed
            1.3.2.1 Kali apache2 server IP in clippy image directory field
            1.3.2.2 Executable field with url to Firefox.exe on server
        1.3.3 Interact with empire agent
    1.4 Fake macOS update (OR)
        1.4.1 macOS trojan with firefox installer and Empire backdoor (.zip) (AND)
        1.4.2 BeEF social engineering Fake notification bar command executed
            1.4.2.1 url to Firefox.zip on apache2 server
            1.4.2.2 Fitting message
        1.4.3 Interact with empire agent  
    1.5 Fake Linux update
        1.5.1 Linux trojan 
        1.5.2 BeEF social engineering Flash update command executed    
            1.5.2.1 Kali apache2 server IP in image field
            1.5.2.2 Custom_Payload
            1.5.2.3 url to flash-update.deb on apache2 server on Kali
        1.5.3 Interact with empire agent
```

## Notes

* Fake Linux Firefox update does not work for Ubuntu 22.04+. Is now a snapd.
* Many more possibilities, with other commands as well. Get creative.

## Tools

* [BeEF in Kali](https://www.kali.org/tools/beef-xss/)