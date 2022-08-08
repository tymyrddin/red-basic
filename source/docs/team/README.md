# Introduction

## What?

Red teaming is a full-scope, multi-layered attack simulation, in the forest.

## Why?

Measure how well people and networks, applications, and physical security controls can withstand an attack from a real-life adversary.

* Flexible methodologies
* The security teams of the organisations have no information about it happening
* Attacks can happen 24/7
* Measure the impact of the vulnerabilities

## How?

By role playing a likely adversary and adopting their ways of thinking, working, and tools.

[In the grove](../lab/README.md) we have been using tools such as the Metasploit Framework, routersploit, enumeration 
tools, nmap, and so on for post-exploitation and scanning, and PowerShell was a really great playground.

But nowadays outside-of-the-testlab-box, even if you encode the PowerShell command into base64 or any other encoder, 
the payload delivery still gets detected by hard implementation of the group policies and by AntiVirus with ML and AI, 
which detects the intrusion by a mere execution of the powershell.exe program.

For red teaming in the wild, we will switch to another set of tools:

* *nix-based system (Kali, Ubuntu, or macOS)
* [C&C](C2.md)
* [MSFvenom Payload Creator](msfvenom.md)
* [Empire](empire.md)
* [Koadic](koadic.md)




