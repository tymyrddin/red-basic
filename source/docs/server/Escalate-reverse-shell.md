# Escalate a reverse shell to a weevely shell

# Attack tree

```text
1 Get current privileges (whoami, uname -a, ls, pwd, cat etc/passwd)
2 Generate backdoor with weevely (.txt)
3 Upload to any server (with a direct URL)
4 Download it to target server
5 Rename the backdoor to .php
5 Start listener on hacking machine
5 Connect to hacking machine from target server
```


## Cheatsheets

* [Linux post exploitation enumeration](cheatsheets:docs/enumeration/linux-post)

