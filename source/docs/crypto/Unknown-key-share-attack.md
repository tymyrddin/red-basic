# Unknown key share attack

A unknown key share attack is an oldie in authenticated key agreement protocols: one of two people are coerced into sharing a key between them, when either or both believe they are sharing the key with another, a third person.

## Attack tree

As an example, suppose two people, Nina and Isabelle, have already established a pairwise E2EE session. A malicious user establishes another E2EE session with Nina. Nina apparently trusts both Isabelle as well as the adversary. Isabelle and the malicious user can be friends or colleagues of Nina. Isabelle may not share in this trust, maybe does not even know the malicious user. The adversary tries to establish a fake E2EE session with Nina where the Key and Initialisation Vector are the same as those used in the already established session:

```
1 Retrieve a public key from the msg application server (AND)
2 Register the key with the server (AND)
3 Request a new E2EE session with Nina 
```

As a result, Nina's device computes a shared secret for the one-to-one (which is the same as the shared secret between Nina and Isabelle). The adversary does not know the Shared Secret because he or she does not have the secret key, but IF there is no key confirmation in the client-to-client key exchange phase of the protocol, it will not abort, and an E2EE session will be established between Nina and the adversary. Under these conditions, even a normal user, who is not an E2EE adversary, is able to perform the attack.

After this malicious key exchange, the adversary can send a packet to Isabelle (which was originally sent from Nina to the adversary) by impersonating Nina. The malicious user can also send a message to Nina by impersonating Isabelle.

## Mitigation

Mitigation involves implementing the key confirmation phase after the key exchanges (the message exchanging session does not start if the two parties do not correctly share their secret values) and guaranteeing the integrity of associated data (even if a malicious key exchange succeeds, the adversary is not able to change sender key ID and recipient key ID).

This attack does not work in Signal because the computation of a shared secret in the key exchange phase involves One-Time Pre Key. This changes the shared secret at every execution of the key exchange even if the public keys are the same.

