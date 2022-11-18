# Simple macOS trojan

## Attack tree
```text
1 Backdoor (AND/OR)
2 Keylogger (AND/OR)
3 Password recovery tool (AND)
4 Make simple trojan (AND)
    4.1 Evil file
        4.1.1 Configure evil file to download and execute a normal file (AND)
        4.1.2 Compile and change icon (in Cocoa) (AND)
        4.1.3 Configure to run silently (add key and value in info.plist)
    4.2 Embed code (usestager osx/macro)
4 Deliver payload (AND)
5 Listen and post exploitation
```

## Notes

### Preview document icons
Problem: macOS "finder ready" icons give a preview of the document file.

Solution: Make them yourself with screenshots. My assumption is that developers running Linux for developing apps will 
buy a Mac just for creating some icon files. Converters will exist, that can also make "finder ready" icons from png
images.

New problem:
* The Iconvert icons website is not found (is either down or has been removed). 
* The page for downloading the demo version of it on Softpedia and the Internet Archive are an archeological site with empty download (so we can all remember its existence).
* The `icnsutils` package, which contains `png2icns` and `icns2png`, does not do "finder ready" `.icns`, so the results are squared. Useful for building app Trojans for iPhones for example, but not for preview pdf icons.
* GIMP no longer has built-in support for creating `.icns` and the GIMP registry is no longer maintained which means that finding [plugins](https://shotkit.com/gimp-plugins/) can be quite the challenge. 
* I found the [Gimp Mac Helper, but it is old](https://osdn.net/projects/sfnet_gimp-mac-helper/) and specifically mentions supporting GIMP 2.
* There are free tools on the Apple Store that can do it, but one has to sign up for an Apple Account and provide credit card information (something I efinitely do not want to provide to anyone on the Internet (or phone for that matter))

Solution: Use old version of Image2Icon - - Download on the macOS, drop in the `.png` and use the export to icns (not using any templates)

## Tools

* [Icon brew](https://iconbrew.com/)
* [Image2Icon](https://download.cnet.com/Image2icon/3000-2195_4-76407711.html)

