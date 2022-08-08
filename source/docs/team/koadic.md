# Koadic

PowerShell was a really great playground in the grove.

But nowadays outside-of-the-testlab-box, even if you encode the PowerShell command into base64 or any other encoder, 
the payload delivery still gets detected by hard implementation of the group policies and by AntiVirus with ML and AI, 
which detects the intrusion by a mere execution of the powershell.exe program.

* Koadic does not use PowerShell for post-exploitation, it supports scripting such as VBScript and JScript. 
* Koadic does not rely on TCP connections for continuous communication. The connection is maintained by requesting
multiple HTTP connections.
* An implant is a JavaScript or a VBScript code, to be executed by zombies to perform a certain task, like the post 
modules in Metasploit. The implants are categorised: pivot, persistence, manage, utils, elevate, gather, scan, fun, 
and inject.

## Requirements

Python package version 2 or 3

## Install

    git clone https://github.com/zerosum0x0/koadic

Install the python packages koadic depends on:

    sudo pip install -r requirement.txt

Start her up with:

    ./koadic

Koadic starts with the MSHTA stager as the default stager. The Microsoft HTML 
Application (MSHTA) is a full-grown Microsoft Windows HTML application that is trusted 
by the developer who creates it. It's like the Internet Explorer browser but without the user 
interface or any strict security model. It displays only a few options, such as menus, icons, 
title information, and toolbars.

## Usage

### A Koadic-style post-exploitation

1. Stager Establishment: Set up the stager web server where the zombie will get connected.
2. Payload Execution: Drop the payload over to the target server and execute the payload to get the zombie hooked up 
by Koadic.
3. Running Implants: Execute the implants to get domain information, SYSTEM access, and NTLM hashes. These can be used 
for further post-exploitation.
4. Pivoting: Hook the zombie and move around the network through it.