# Bettercap starts with SSL strip disabled

```shell
@kali:~$ sudo bettercap -iface eth0 -caplet hstshijack/hstshijack

------------------------------------

[sudo] password for <user>: 
bettercap v2.32.0 (built for Linux amd64 with go1.15.15) [type 'help' for a list of commands]

2022-01-23 14:36:56 inf hstshijack Generating random variable names for this session ...
...
[snip]
...
[14:36:56] [sys.log] [inf] http.proxy enabling forwarding.
[14:36:56] [sys.log] [inf] http.proxy started on 192.168.122.108:8080 (sslstrip disabled)
...
```

Disabled. Solution: First start Bettercap, then set proxy with sslstrip and then hstshijack:

```shell
@kali:~$ sudo bettercap -iface eth0

...

192.168.122.0/24 > 192.168.122.108  » set http.proxy.sslstrip true
192.168.122.0/24 > 192.168.122.108  » hstshijack/hstshijack
```
