# Simple Linux trojan

## Attack tree
```text
1 Backdoor (AND/OR)
2 Keylogger (AND/OR)
3 Password recovery tool (AND/OR)
4 ZReporter (AND)
5 Make simple trojan (AND)
    5.1 Embed evil code in an executable linux package (OR)
        5.1.1 On packages website of distro, select OS version of target machine, web software, and for example, a flash plugin (AND)
        5.1.2 Download package (AND)
        5.1.3 dpkg it (AND)
        5.1.4 ar it (to get the control and postinst files, and move to a new directory in the unpackaged package) (AND)
        5.1.5 Modify the postinst (AND)
        5.1.6 Pack it back up (AND)
    5.2 Embed evil code in an android app
        5.2.1 On app site (APK for example) select an app (AND)
        5.2.2 For some dependencies if need be, update alternatives (AND)
        5.2.3 Generate android backdoor (android/meterpreter/reverse_http, latest method) in the apk with fatrat (AND)
        5.2.4 Set bridged adapter in network settings to add the kali machine to the wifi network (AND)
        5.2.5 Listen with metasploit multi handler (msfconsole)
6 Deliver payload (AND)
7 Listen and post exploitation
```

## Notes

### Packaging

Problems: Executables do not run by double click and users have to manually change file permission to executable.

Solution :
* Embed evil code in an executable package.
* Use a legitimate app to make the trojan less suspicious.
* One that runs by doubleclicking with root (admin) privileges.

### Creating An Android Trojan

* Embed a backdoor in a normal app.
* Everybody makes apps these days.
* Pretend to be a friend and send the app to the target.
* When the app is executed, the user will see a functional app but at the same time our backdoor will run in the background.

## Tools

* [Ubuntu Packages](https://packages.ubuntu.com/)
* [APK Mirror](https://www.apkmirror.com/)


