# Chosen plaintext attack

In a chosen-plaintext attack an adversary can (possibly adaptively) ask for the ciphertexts of arbitrary plaintext messages. This is formalized by allowing the adversary to interact with an encryption oracle, viewed as a black box. The goal is to reveal all or part of the secret encryption key.

* It may seem infeasible in practice that an attacker could obtain ciphertexts for given plaintexts, but modern cryptography is implemented in software or hardware and is used in a diverse range of applications and very feasible. Chosen-plaintext attacks become extremely important in the context of public key cryptography, where the encryption key is public and so attackers can encrypt any plaintext they choose.
* Chosen-plaintext attacks (CPAs) are often used to break symmetric encryption. Thus, it is important for symmetric cipher implementers to understand how an attacker would attempt to break their cipher (and make improvements based on that).
* For some chosen-plaintext attacks, only a small part of the plaintext may need to be chosen by the attacker; such attacks are known as plaintext injection attacks.

## Attack tree

```
1 Choose a set of plaintexts and submit once to the oracle (batch chosen-plaintext attack)
2 Choose a smaller one, receive its encrypted ciphertext and then based on the answer, 
choose another one (when having the capability to choose plaintext for encryption many 
times and instead of using one big block of text) (adaptive chosen plaintext attack)
```

## Resources

* [Bleichenbacher's attack](https://asecuritysite.com/encryption/c_c3)

## Encryption oracles

A cryptographic oracle is a mathematical description of a data leak, to be used in security proofs. Given access to such an oracle, it is possible to rebuild the private key. For example, in the old (1999) case of RSA, it meant that knowing whether a value has a proper padding or not is equivalent to learning the private key (after a million or so tries). The Bleichenbacher attack showed that it also works the other way round.

In cryptographic papers oracles are often used to show that, even if adversaries would have access to an oracle, they still wouldn't have any (significant) advantage for breaking security. For example, one important property of encryption algorithms (called resistance to known plaintext attacks) is that if an attacker is given a message encrypted with a key m' and they want to know the original message m (or figure out the key), then giving them another message n and its encryption with a key n' should not help them do so.





