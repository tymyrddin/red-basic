# Brute-force and dictionary attacks

## Attack tree

```text
1 Make a users.txt file from enumerated users
2 Make a passwords.txt file (use information from reconnaissance)
3 Use a tool such as Metasploit, Hydra, Medusa, or Nmap
```

## Examples

### SSH

`users.txt` contains one entry: a name from users enumeration

    nmap --script ssh-brute -p22 <IP address> --script-args userdb=users.txt,passdb=passwords.txt

## Notes

In a brute-force attack, an adversary cycles through every possible password combination until they stumble on the 
correct one. The time required is likely to exceed the death of the universe, and it is most likely to trigger 
automated blocking defenses and set off every possible alarm.

Lists of the most popular passwords and dictionary attacks make the process much quicker than pure trial 
and error. The more sophisticated a user’s password, however, the longer it will take and the more it will cost to 
crack it, and if the password is not in the dictionary of guesses, no luck.

The more guesses made, the more likely is detection or triggering a control. If the target organisation has an 
account lockout policy that locks an account after four incorrect guesses, this may create a denial of service 
condition for any accounts targeted with four or more incorrect guesses.

## Scripts

* [Password guessing](https://github.com/tymyrddin/reomais/blob/main/password_guessing)

## Resources

* [Password lists](https://github.com/berandal666/Passwords)
