# BeEF unable to load extensions

When starting BeEF the first time:

```shell
● beef-xss.service - beef-xss
     Loaded: loaded (/lib/systemd/system/beef-xss.service; disabled; vendor preset: disabled)
     Active: active (running) since Thu 2022-01-20 09:54:46 CET; 5s ago
   Main PID: 98386 (ruby)
      Tasks: 3 (limit: 4612)
     Memory: 74.9M
        CPU: 587ms
     CGroup: /system.slice/beef-xss.service
             └─98386 ruby /usr/share/beef-xss/beef

Jan 20 09:54:47 kali beef[98386]: [ 9:54:47][!] Unable to load extension 'demos'
Jan 20 09:54:47 kali beef[98386]: [ 9:54:47][!] Unable to load extension 'e…nts'
Jan 20 09:54:47 kali beef[98386]: [ 9:54:47][!] Unable to load extension 'r…ter'
Jan 20 09:54:47 kali beef[98386]: [ 9:54:47][!] Unable to load extension 'proxy'
Jan 20 09:54:47 kali beef[98386]: [ 9:54:47][!] Unable to load extension 'n…ork'
Jan 20 09:54:47 kali beef[98386]: [ 9:54:47][!] Unable to load extension 's…ing'
Jan 20 09:54:47 kali beef[98386]: [ 9:54:47][!] Unable to load extension 'x…ays'
Jan 20 09:54:47 kali beef[98386]: -- migration_context()
Jan 20 09:54:47 kali beef[98386]:    -> 0.0029s
Jan 20 09:54:47 kali beef[98386]: [ 9:54:47][*] BeEF is loading. Wait a few…s...
Hint: Some lines were ellipsized, use -l to show in full.

[*] Opening Web UI (http://127.0.0.1:3000/ui/panel) in: 5... 4... 3... 2... 1... 

```

With an error page in browser.

To get BeEF to work on kali:

```shell
kali:~$ sudo apt-get -y autoremove beef
kali:~$ sudo apt-get -y autoremove beef-xss
```

And install with:

```shell
kali:~$ sudo apt-get install beef-xss
```

Then it looks like:

```shell
● beef-xss.service - beef-xss
     Loaded: loaded (/lib/systemd/system/beef-xss.service; disabled; vendor preset: disabled)
     Active: active (running) since Thu 2022-01-20 10:01:23 CET; 5s ago
   Main PID: 99666 (ruby)
      Tasks: 4 (limit: 4612)
     Memory: 71.4M
        CPU: 613ms
     CGroup: /system.slice/beef-xss.service
             └─99666 ruby /usr/share/beef-xss/beef

Jan 20 10:01:23 kali beef[99666]: [10:01:23]    |   Blog: http://blog.beefp….com
Jan 20 10:01:23 kali beef[99666]: [10:01:23]    |_  Wiki: https://github.co…wiki
Jan 20 10:01:23 kali beef[99666]: [10:01:23][*] Project Creator: Wade Alcor…orn)
Jan 20 10:01:23 kali beef[99666]: -- migration_context()
Jan 20 10:01:23 kali beef[99666]:    -> 0.0067s
Jan 20 10:01:23 kali beef[99666]: [10:01:23][*] BeEF is loading. Wait a few…s...
Jan 20 10:01:23 kali beef[99666]: [10:01:23][!] [AdminUI] Error: Could not …_all
Jan 20 10:01:23 kali beef[99666]: [10:01:23]    |_  [AdminUI] Ensure nodejs…H` !
Jan 20 10:01:23 kali beef[99666]: [10:01:23][!] [AdminUI] Error: Could not …auth
Jan 20 10:01:23 kali beef[99666]: [10:01:23]    |_  [AdminUI] Ensure nodejs…H` !
Hint: Some lines were ellipsized, use -l to show in full.

[*] Opening Web UI (http://127.0.0.1:3000/ui/panel) in: 5... 4... 3... 2... 1... 
```

There are still problems regarding `nodejs`, but at least we now get the server.
Installing `nodejs` (mind that bash is called, so this requires root, sudo is not enough)

```shell
kali:~$ sudo -s                                                       
root@kali:/home/<user># curl -fsSL https://deb.nodesource.com/setup_17.x | bash -
root@kali:/home/<user># apt-get install -y nodejs
```
Not that BeEF now "sees" `nodejs`. Not even after a re-install. Still, some functionalities are working and I will get back to this.