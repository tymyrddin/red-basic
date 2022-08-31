# Introduction

## What?

As security and intrusion detection have gotten more sophisticated, so have the tools created and used by adversaries 
and network engineers. The purpose of scanning is to find what hosts are currently active on the network. With probing 
an adversary can gather additional information, such as the OS, technologies used, applications, and their vulnerabilities.

* Locate network range
* Discover active hosts by looking for open ports
* Most common applications use well-defined port numbers. Not always. Probe, research and puzzle further.
* Find and research vulnerabilities of OSs and the applications, defence mechanism, network architecture, infrastructure equipment, etc.
* Make a map of the hosts, servers, and weaknesses to exploit in the future. Keep adding to the map as more is discovered later in the process.

## Why?

Intelligently select tools and exploitation methods for an attack, scanning and enumeration can be used to make sure you:

* Attack only agreed-upon targets
* Get as much information as possible before increasing depth of attack
* Identify purpose and type of targets (what services are provided)
* Have specific information about versions of services running on target systems
* Categorise target systems

## How?

* [Host discovery with ICMP (ping sweep)](icmp.md)
* [Host discovery with TCP](tcp.md)
* [Host discovery with UDP](udp.md)
* [Discover vulnerabilities](vulns.md)
* [Service and OS detection](service-and-os.md)
* [Diving deeper in discovery](analysis.md)