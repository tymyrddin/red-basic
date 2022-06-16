# Brute-force

## Attack tree

```text
1 Obtain packet (to facilitate offline attack) (AND)
2 No password policy (AND)
    2.1 No account lock-out
    2.2 Lack of password complexity
3 Use cracking tool to discover password 
```

## Notes

In a brute-force attack, an adversary cycles through every possible password combination until they stumble on the correct one. Lists of the most popular passwords and dictionary attacks make the process much quicker than pure trial and error. The more sophisticated a user’s password, however, the longer it will take and the more it will cost to crack it.

## Demo scripts

* [Simple crawler](https://github.com/tymyrddin/reomais/blob/main/crawler)
* [Simple spider](https://github.com/tymyrddin/reomais/blob/main/spider)
* [Password guessing](https://github.com/tymyrddin/reomais/blob/main/password_guessing)
