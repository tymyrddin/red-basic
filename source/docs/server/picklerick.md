# Command injection

## Attack tree

```text
1 Enumerate
    1.1 Gobuster
    1.2 Dirbuster
2 Puzzling for clues
```

## Example

This example is from [doing the THM Pickle Rick room](https://tryhackme.com/room/picklerick): We need to find the 
three secret ingredients in order to turn Rick back to his old self.

## One

Enumerate the machine by using Nmap scanner.

    nmap -Pn -Sv -A -v <Machine IP>

Two ports are open on the machine: 80 (HTTP) and 22 (SSH). Try view the site on <Machine IP> and the source code 
for more information. Owww, a note to self with a username: `R1ckRul3s`.

Using gobuster to enumerate:

    gobuster dir -u <Machine IP> -w /usr/share/dirb/wordlists/common.txt

Visiting many places and files. The `robots.txt` file inside the webserver contains `Wubbalubbadubdub`. 
Could be a password. Or just nonsense.

[Enumerating the webserver using dirbuster](https://git.mst.edu/slbnmc/ici-wiki/-/wikis/Enumerating-Web-Server-Files-and-Directories-with-DirBuster) 
gives a `portal.php` gobuster did not list. Visiting the portal site brings a login page.

Trying the found username `R1ckRul3s` and `Wubbalubbadubdub` as password gives a command panel page 
with a form. Perhaps an RCE is possible?

Doing an `ls` shows the first secret ingredient file and a `clue.txt`, BUT, `cat` is disabled. So try `less` instead. 
Boom!

### Two

And the `clue.txt` file indicates there is another ingredient file hidden inside the file system. 

    ls -la /home/rick

Ha!

### Three

    sudo- l

results:

    (ALL) NOPASSWD: ALL

No password on sudo, sooo:

    sudo ls -la /root

Found.


    