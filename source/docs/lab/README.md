# Introduction

## What?

Set up and maintain a local test lab for safely playing around in, a grove in the forest. 

## Why?

For the grove, we just provide a convenient way for: 

* Grokking systematic hacking
* Building hacking skills
* Getting to know typical software used

All the while staying out of legal trouble, and guaranteeing that the effects of the hacking are limited to the lab 
hardware and software.

## How?

Use virtualisation and containerisation. If you do not have virtualisation, you can set up a lab with a few old buckets. 
If the machine you are on supports virtualisation, you can use VMWare and ready-made guests, or use KVM and make the 
virtual machines yourself. Do not run both virtualisation solutions (VMWare and KVM) at the same time, or turn off one in `systemctl` when using the 
other. Switching is a hassle though.

### Attacker
* A [Kali machine](Kali.md): The Kali machine serves as attack machine, as development machine for hacking-related scripts, and for using its apache2 webserver to serve hooks and files.
* [Mitre Att&ck Caldera](caldera.md)

### PC targets
* One or two [Windows PC machines](Windows.md), both 10 or a 10 and an 11 machine: 
  * One of the two serves as development machine for scripts that are best developed on the target they are meant for. This machine will need Python installed on it. 
  * The second one, if created, can be used to test binaries, and does not need to have Python installed.
* A [macOS machine](macOS.md), choose Catalina, Big Sur or Monterey based on reconnaissance, or just Catalina.
* A [Linux PC machine](Linux.md), choose distro depending on reconnaissance, or just Debian and friends (which include Ubuntu and Mint).

### Targets
* [Metaspoitable machine](Metasploitable.md): The metasploitable provides targets for the most simple (mostly php) attacks.
* [Webgoat and wolf machine](Webgoat.md), a deliberately insecure application that allows for testing vulnerabilities commonly found in JS-based applications that use common and popular open source components.
* [Any of these](https://github.com/sparcflow/awesome-cyber-skills), a curated list of hacking environments where you can train your cyber skills legally and safely.

WARNING 1: While running target machines, the local machine will be extremely vulnerable to attack. Disconnect 
from the Internet while using. WebGoat’s default configuration binds to localhost to minimize the exposure.

WARNING 2: The target machines are for educational purposes only. 
