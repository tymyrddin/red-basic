# Red team: create a botnet

From research, what appears to be happening.

## Attack tree

```text
1 Set up a command-and-control infrastructure
    1.1 Set up a webserver (AND)
    1.2 Get a botnet builder tool for malware such as Ice IX (AND)
    1.3 Set up the parameters (AND)
        1.3.1 How often the zombie is to communicate with the command server (AND)
        1.3.2 What actions to take (AND)
        1.3.3 How to hide from anti-virus scans (AND)
        1.3.4 Location of its control and command server
    1.4 Upload command-and-control to server
2 Make payload file (AND)
    2.1 Crypt and pack
3 Spread file
    2.1 Phishing (OR)
    2.2 Install using MitM (targeted attack) (OR)
    2.3 Credential stuffing (buy credentials that have been leaked through data breaches or other means)
    2.4 Other tactics
```

## Notes

A botnet (“robot network”) is a network of computers infected by malware that are under the control of a single attacking party.

Botnets are typically used in:

* Email spam campaigns. These botnets are the largest. The spam messages can include malware, and can also be used to recruit more computers to the botnet.
* [DDoS attacks](../network/DDoS.md) that target organisations for personal or political motives or to extort payment in exchange for ceasing the attack.
* [Credential stuffing](Credential-stuffing.md) to gain access to accounts from data breaches to drain the associated accounts of stored values, credit card information, personally identifiable information and/or to use the account for impersonation, and for actions like sending spam.
* Targeted intrusions where typically small botnets compromise high-value systems of organisations from which attackers can penetrate and intrude further into the network. With just one zombie in an organisation, the adversary can now read email and monitor traffic and communications for sniffing out passwords, identifying databases, and looking for users with more administrative powers. The assets an adversary can look for include password databases, financial data, research and development, intellectual property, and customer information. Botnet infiltration works incredibly fast because most people will trust files that appear to have originated with other employees inside the network and will pass along files from sources they know. A botnet is not just a malware infection, it is like having an adversary inside the network.

## Articles

* [Most Dangerous Botnets That are Still in the Game](https://cloudtweaks.com/2022/01/most-dangerous-botnets/), CloudTweaks, 2022
* [Why Current Botnet Takedown Jurisprudence Should Not Be Replicated](https://www.lawfareblog.com/why-current-botnet-takedown-jurisprudence-should-not-be-replicated), LawFare, 2021
* [MasterBlaster: Identifying Influential Players in Botnet Transactions](https://sefcom.asu.edu/publications/masterblaster-identifying-influential-compsac2011.pdf), IEEE 2011 but with a nice explanation of components