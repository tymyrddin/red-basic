# Introduction

## What?

Red teaming is a full-scope, multi-layered attack simulation, in the forest. It is meant to measure how well people 
and networks, applications, and physical security controls can withstand an attack from a real-life adversary.

[In the grove](../lab/README.md) we have been using tools such as Metasploit, Routersploit, Nmap, Empire, and so on 
for post-exploitation and scanning. For red teaming in the forest, some of these tools are still useful, but for others 
we will have to switch to other tools.

## Why?

* The security of the tooling, the anonymity of the infrastructure, and how-to-stay-safe is becoming increasingly 
important in the ever-increasingly authoritarian world we seem to be forging for ourselves. We will not be stamping 
around in a little safe-like grove, we will need way more stealth to not be detected in the forest by the blue team.
* For the best part of the last decades the undefeated champion of C2 frameworks was the Metasploit framework, but the 
default settings of the tool have been flagged by every security product since 2007. For hacking Linux PC's it 
can still be a good choice, but for Windows targets the techniques employed by the meterpreter are first on the 
checklist of just about every antivirus software.
* The Empire framework provides an exhaustive list of modules, exploits, and lateral movement techniques specifically
designed for Active Directory. It is no longer maintained by the original team, and BC Security, released version 3.0 
in December 2019. The framework assumes that PowerShell allows attackers unhindered access to the environment. As of 
Windows 10, with PowerShell block logging and AMSI, this is no longer the case.

## How?

* [Using a VPN](vpn.md)
* [Location, location, location](location.md)
* [Ephemeral OS](ephemeral.md)
* [Bouncing servers](bouncing-servers.md)
* [Infrastructure frontend](frontend.md)
* [Metasploit container for Linux targets](metasploit.md)
* [SILENTTRINITY for Windows targets](silenttrinity.md)
* [IP masquerading](masquerading.md)
* [Automating the server setup](automation.md)





