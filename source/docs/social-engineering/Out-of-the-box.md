# Getting out of the box

## Attack tree

```text
1 Port forwarding
    1.1 Backdoor with public IP and port 8080 (for example) (AND)
    1.2 Listen on local IP port 8080 (AND)
    1.3 Set port forwarding on router for receiving msg from backdoor (AND)
        1.3.1 Public port range (8080) (AND)
        1.3.2 Address local machine (192.168.122.108) (AND)
        1.3.3 Target port range (8080) (AND)
        1.3.4 Protocol (Both, or TCP)
    1.4 Set port forwarding on router for allowing download of evil files from apache2 server (AND)
        1.4.1 Public port range (80) (AND)
        1.4.2 Address local machine (192.168.122.108) (AND)
        1.4.3 Target port range (80) (AND)
        1.4.4 Protocol (Both, or TCP)
    1.5 Change BeEF script to use public IP (AND)
    1.6 Set port forwarding on router for BeEF
        1.6.1 Public port range (3000) (AND)
        1.6.2 Address local machine (192.168.122.108) (AND)
        1.6.3 Target port range (3000) (AND)
        1.6.4 Protocol (Both, or TCP)
2 DMZ Kali machine
    2.1 Enter local IP address of Kali machine
```

## Notes

### Alternatives

* Installing Kali/Tools in the cloud
* Port forwarding using an SSH server
* Tunneling services