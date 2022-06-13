# Read a PGP encrypted message

## Attack

```
1 Decrypt the message itself (OR)
    1.1 Break asymmetric encryption (OR)
        1.1.1 Brute force break asymmetric encryption (OR)
        1.1.2 Mathematically break asymmetric encryption (OR)
            1.1.2.1 Break RSA (OR)
            1.1.2.2 Factor RSA modulus/calculate ElGamal discrete log 
        1.1.3 Cryptanalyse asymmetric encryption
            1.1.3.1 General Cryptanalysis of RSA/ElGamal (OR)
            1.1.3.2 Exploiting weaknesses in RSA/ElGamal (OR)
            1.1.3.3 Timing attacks on RSA/ElGamal
    1.2 Break symmetric key encryption
        1.2.1 Brute force break symmetric key encryption (OR)
        1.2.2 Cryptanalyse symmetric key encryption
2 Determine symmetric key used to encrypt the message via other means
    2.1 Fool sender into encrypting message using public key whose private key is known (OR)
        2.1.1 Convince sender that a fake key (with known private key) is the key of the intended recipient
        2.1.2 Convince sender to encrypt using more than one key–the real key of the recipient, and a key whose private key is known
        2.1.3 Have the message encrypted with a different public key in the background, unbeknownst to the sender
    2.2 Have the recipient sign the encrypted symmetric key (OR)
    2.3 Monitor computer memory of sender (OR)
    2.4 Monitor computer memory of recipient (OR)
    2.5 Determine key from pseudorandom number generator (OR)
        2.5.1 Determine state of randseed.bin when message was encrypted (OR)
        2.5.2 Implant malware (virus) that deterministically alters the state of randseed.bin (OR)
        2.5.3 Implant software that directly affects the choice of symmetric key
    2.6 Implant malware (virus) that exposes the symmetric key
3 Get recipient to (help) decrypt the message (OR)
    3.1 Chosen ciphertext attack on symmetric key (OR)
    3.2 Chosen ciphertext attack on public key (OR)
    3.3 Send the original message to the recipient (OR)
    3.4 Monitor outgoing mail of recipient (OR)
    3.5 Spoof Reply-To: or From: field of original message (OR)
    3.6 Read message after it has been decrypted by recipient.
        3.6.1 Copy message off user's hard drive or virtual memory (OR)
        3.6.2 Copy message off backup (OR)
        3.6.3 Monitor network traffic (OR)
        3.6.4 Use electromagnetic snooping techniques to read message as it is displayed on the screen (OR)
        3.6.5 Recover message from printout
4 Obtain private key of recipient
    4.1 Factor RSA modulus/calculate ElGamal discrete log (OR)
    4.2 Get private key from recipient's key ring (OR)
        4.2.1 Obtain encrypted private key ring (AND)
            4.2.1.1 Copy it from user's hard drive (OR)
            4.2.1.2 Copy it from backups (OR)
            4.2.1.3 Monitor traffic (OR)
            4.2.1.4 Implant malware (virus/worm) to expose copy of the private key
        4.2.2 Decrypt private key
            4.2.2.1 Break IDEA encryption (OR)
                4.2.2.1.1 Brute-force break IDEA (OR)
                4.2.2.1.2 Cryptanalysis of IDEA (OR)
            4.2.2.2 Learn passphrase
                4.2.2.2.1 Monitor keyboard when user types passphrase (OR)
                4.2.2.2.2 Convince user to reveal passphrase (OR)
                4.2.2.2.3 Use keyboard logging software to record passphrase when typed by user (OR)
                4.2.2.2.3 Guess passphrase 
    4.3 Monitor recipient's computer memory (OR)
    4.4 Implant malware (virus) to expose private key
    4.5 Generate insecure private/public key pair for recipient
```
## Resources

* [Reading a PGP encrypted message](https://www.schneier.com/academic/archives/1999/12/attack_trees.html), Schneier

