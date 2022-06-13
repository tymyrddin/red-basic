# Chosen ciphertext attack

In a chosen-ciphertext attack (CCA), an adversary can analyse chosen ciphertexts together with their corresponding plaintexts to acquire a secret key or to get as many information about the system as possible. In this attack, the adversary is assumed to have a way to trick someone who knows the secret key into decrypting arbitrary message blocks and send back the result. The attacker can choose some arbitrary nonsense as an “encrypted message” and ask to see the (usually) different nonsense it decrypts to, and can do this a number of times. The goal of the adversary is deducing what the secret key is.

* Chosen-ciphertext attacks are usually used for breaking systems with public key encryption. Early versions of the RSA cipher were vulnerable to such attacks. They are hardly used for attacking systems protected by symmetric ciphers, but some self-synchronising stream ciphers can also be attacked successfully.
* An adaptive chosen-ciphertext attack (CCA2) is an interactive form of chosen-ciphertext attack in which an adversary first sends a number of ciphertexts to be decrypted chosen adaptively, then uses the results to distinguish a target ciphertext without consulting the encryption oracle on the challenge ciphertext. There exist rather few practical adaptive-chosen-ciphertext attacks. This model is mostly used for analysing the security of a given system. Proving that this attack doesn't break the security confirms that any realistic chosen-ciphertext attack is unlikely to succeed. In an adaptive attack the attacker is allowed adaptive queries after the target is revealed (but the target query is disallowed). In an indifferent (non-adaptive) chosen-ciphertext attack (CCA1), the second stage of adaptive queries is not allowed. 

## Attack tree

```
    1 Replace or modify a ciphertext to be sent on a device (AND)
    2 Eavesdrops on the communications (AND)
    3 Work out what the receiver read when he/she decrypted the fake ciphertext
```



