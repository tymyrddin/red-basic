# Password spraying

## Attack tree

```text
1 Make a users.txt file from enumerated users
2 Choose a well-known likely password (use information from reconnaissance, season)
3 Use a tool such as Metasploit, Hydra, Medusa, or Nmap
```

## Examples

### SSH

    hydra -L userlist.txt -p Password123! <target IP> ssh

## Notes

The disadvantages are that it relies heavily on luck and good educated guesses about how people think, and there
is still a risk of alarms going off because of targeting many accounts from a single source or over a small amount of 
time.