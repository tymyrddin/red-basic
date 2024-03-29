# Simple Windows trojan

## Attack tree
```text
1 Backdoor (AND/OR)
2 Keylogger (AND/OR)
3 Password recovery tool (AND)
4 Make simple trojan (AND)
    4.1 Use Powershell script (OR)
        4.1.1 Combine evil file(s) with normal file
        4.1.2 Convert evil.bat files to .exe (for silently running in background and create and add icon)
        4.1.4 Spoof file extension 
            4.1.4.1 with RLO
            4.1.4.2 with WinRAR zip and hexeditor
    4.2 Use AutoIt script (OR)
        4.2.1 Combine evil file(s) with normal file
        4.2.2 Convert evil.au3 files to .exe (and create and add icon)
        4.2.3 Can zip it (but most people don't look)
    4.3 Embed code (usestager windows/macro)
4 Deliver payload (AND)
5 Listen and post exploitation
```

## Notes

### Spoofing file extensions on Windows

The hard part in this method is the spoofing of the file extension. 

In Windows, there is a setting in Folder Options where the file extension can be hidden so that only the filename is 
visible in Explorer while the extension is hidden. The problem with this setting is the default option is set to hide 
and a less careful user can be tricked when there is a double extension. An example of a double extension is:

    notes.txt.exe

will show up as `notes.txt`. File type is still application (change the view type to "Details"). And a few antivirus 
applications will warn for it. Defender may even remove it.

The Right to Left Override unicode trick reverses the last six characters so that the extension is spoofed. The 
`notes.exe` file can be renamed to `notesexe.txt`, but the Windows operating system still recognizes the file as an 
application. Most major web browsers blacklist the right to left override character so that the correct file extensions 
are shown when a user attempts to download the file with a spoofed extension using the RTLO trick.

Older versions of WinRAR 4.20 are vulnerable to file name and extension spoofing. This means it is possible to modify 
the ZIP file created by WinRAR 4.20 using a hex editor to show a different filename and extension in the GUI but 
another different extension when it is run directly from the program. Compress the `notes.exe` file into a `notes.zip` 
using WinRAR 4.20 on Windows and using a hex editor, at the end of the file, modify the `notes.exe` to `notes.txt`.

Doubleclicking on the spoof file from WinRAR GUI will run the file as application. However, people who extract the 
file will be safe from this spoofing exploit as they will see that it is an executable (`.exe`) file being extracted, not 
a text (in this case `.txt`) file.

## Tools

* [Bat to Executable (B2E)](https://github.com/tokyoneon/B2E/blob/master/Bat_To_Exe_Converter.zip)
* [PNG to ico](https://cloudconvert.com/png-to-ico)
* [Icon archive](https://iconarchive.com/)
* [RLO Unicode](https://unicode-explorer.com/c/202E)
* [Archive WinRAR V4.20](https://archive.org/details/WinrarV4)
* [AutoIt Scripting Language](https://www.autoitscript.com)
