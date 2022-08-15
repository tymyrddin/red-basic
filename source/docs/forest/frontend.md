# Infrastructure frontend

The attack infrastructure frontend interacts with the target and must be unique to each operation or target, and 
replaced every few days.

It initiates connections to the target, scans machines, and can be used to route incoming packets from a reverse 
shell through a web proxy and deliver them to the backend systems, a C2 framework like Metasploit or SilentTrinity.

This packet routing can be done with a regular web proxy like Nginx or Apache that acts as a filter: requests from 
infected computers are routed to the corresponding backend C2, while the remaining requests are displayed an innocent
web page.