# Escalate a reverse shell to a more powerful shell

## Attack tree

```text
1 Enumerate environment and current privileges (AND)
2 Generate backdoor (with weevely for example) (.txt) (AND)
3 Upload to any server (with a direct URL) (AND)
4 Download it to target server (AND)
5 Rename the backdoor to original extension (AND)
6 Start listener on hacking machine (AND)
7 Connect to hacking machine from target server (AND)
8 Postexploitation
```

## Cheatsheets

* [Shells](cheatsheets:docs/payloads/shells)
* [Linux post exploitation enumeration](cheatsheets:docs/enumeration/linux-post)
* [Windows post exploitation enumeration](cheatsheets:docs/enumeration/windows-post)
* [Spawning a TTY Shell](https://netsec.ws/?p=337) (when using `nc`)

