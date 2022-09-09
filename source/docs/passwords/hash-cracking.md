# Hash cracking

## Attack tree

```text
1 Using hashcat
    1.1 Go to the hashcat website to identify the type of hash function and associated module value.
    1.2 Get the rockyou.txt file (if not already available in /usr/share/wordlists/) 
    1.3 Apply the hashcat command
2. Using Rainbow Tables
    1.1 Identify the type of hash
    1.2 Download or generate the rainbow table
    1.3 Apply command
```

## Example

The `/etc/shadow` file stores the garbled or hashed values of all user's passwords on Linux. It is a critical file 
with strict access permissions; it is and must only be accessible by the root account. If you come across a readable 
`/etc/shadow` file through any regular user account, you can get the hash value of the root account and crack the 
password hash using the hashcat utility.

```text
cut -d: -f1 /etc/shadow | grep root
root:$6$j9T$TANXgpk59y8r3jgPbDl/w/$UqiK6yahwqfyqhcegWLa1.z64TyePP5.VQpUnLqI3VD:18765:0:99999:7:::
```

Save the hash in a file called `hash.txt` and identify the type of hash. SHA512 hash mode is generally identified by 
the $6$ term and has a reference module value of 1800.

```text
hashcat -m 1800 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
```

## Notes

Passwords may be sent over the wire or stored in hashed format. You may intercept one or more of these hashes 
while pursuing other network attacks, for example, with [Responder](red-network:docs/name-resolution/llmnr-netbios). 
Unlike password spraying, you do not risk account lockouts or alert triggers by cracking a hash offline.

### Hash functions

A cryptographic hash function is a type of algorithm that takes variable-length strings (message) of input and
turns them into fixed-length hash values (message digest). The primary objective is message integrity, such that 
the hash value cannot be returned to its original string value. This makes hashing an ideal candidate for storing 
passwords. 

The hash-identifier Python script helps fingerprint various hash types by evaluating characteristics from the known 
hash value.

### Rainbow tables

A rainbow table computes the possible hash values for plaintext values, up to a certain length. Regardless of 
computing power, these tables can become massive and require enormous storage capacity (~300 GB). Each table is 
usually strategically designed for a specific hash requirement, such as MD5, SHA-1, and NT Lan Manager
(NTLM), which is used in various Microsoft network protocols for authentication.

Rainbow tables can be defeated by salted hashes, if the hashes are not salted however, and you have the correct table, 
a complex password can be cracked in a few minutes.

There are various locations you can download Rainbow Tables, for example you can find a fairly comprehensive set of 
free Rainbow Tables at Project RainbowCrack including paid tables optimized for various things (NTLM, MD5, SHA1 etc). 
Project Shmoo is offering downloads of popular Rainbow Tables via BitTorrent.

The tool to generate Rainbow Tables comes with the RainbowCrack download and is called `rtgen`.

### No resources

If you don’t have a high-performance computing system composed of graphics processing unit (GPU) clusters for 
Hashcat or RainbowCrack, using wordlists is a quick and dirty way to find out what you are working with in regard to 
overall security.

You can also try a hash lookup service like Hashes.com. You can put in an MD5, SHA-1, Vbulletin, Invision Power Board,
MyBB, Bcrypt, Wordpress, SHA-256, SHA-512, MYSQL5 etc. hash and search for its corresponding plaintext ("found") in 
their database of already-cracked hashes.

## Tools

* [Hashcat](https://www.kali.org/tools/hashcat/)
* [RainbowCrack](https://www.kali.org/tools/rainbowcrack/)
* [Hashes.com](https://hashes.com/en/decrypt/hash)

## Resources

* [hash-identifier](https://www.kali.org/tools/hash-identifier/)
* [rockyou.txt](https://github.com/redfiles/rockyou.txt)
* [Generic hash types](https://hashcat.net/wiki/doku.php?id=example_hashes)
* [RainbowCrack project: List of Rainbow Tables](http://project-rainbowcrack.com/table.htm)
* [Shmoo rainbow tables](http://rainbowtables.shmoo.com/)
* [Comparison of Hash Function Algorithms Against Attacks: A Review](https://thesai.org/Downloads/Volume9No8/Paper_13-Comparison_of_Hash_Function_Algorithms.pdf)