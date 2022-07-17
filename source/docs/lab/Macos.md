# macOS

## Using VMWare

MacOS can be installed on a VMware VM running on ESXi. This can be done after the preparation of a bootable installation image of the ISO format with hdiutil, applying a free patch on an ESXi server and configuring certain VM settings.
* [Archive: macOS ISO Collection (10.10.5 - 13.0 developer seed)](https://archive.org/details/macos-collection)
* [Creating an (almost) perfect Hackintosh VM](https://shank-s.medium.com/creating-almost-perfect-hackintosh-vm-17126f5328b8)

## Using KVM

* [Apple's Security Bounty program](https://developer.apple.com/security-bounty/requirements/)
* [KVM Opencore](https://github.com/thenickdude/KVM-Opencore)
* [OpenCorePkg](https://github.com/acidanthera/OpenCorePkg)
* [OSX-KVM](https://github.com/kholia/OSX-KVM)
* [How to use Docker-OSX running macOS VM on Linux](https://www.youtube.com/watch?v=wLezYl77Ll8)

## Dockers

* [sickcodes/docker-osx](https://hub.docker.com/r/sickcodes/docker-osx)

## Notes

Installing OS X in a virtual machine is not illegal, but unless you’re using a Mac, it is against Apple’s EULA. Most 
virtual machine software will try to stop you from installing OS X in a VM unless you’re on a Mac. 

A macOS VM is called a Hackintosh. According to Apple, Hackintosh computers are illegal, per the Digital Millennium 
Copyright Act, and creating a Hackintosh computer violates Apple’s end-user license agreement (EULA) for any operating 
system in the OS X family. But, Apple doesn’t care about stopping Hackintosh as much as they do jailbreaking, because 
jailbreaking requires that the iOS system be exploited to gain root privileges, these exploits allow for arbitrary code 
execution with root.

In the context of our local testlab and for our purpose of learning pentesting and/or preparing for red teaming, the 
auto docker (Catalina) will do:

```text
# 40GB disk space required: 20GB original image 20GB your container.
docker pull sickcodes/docker-osx:auto

# boot directly into a real OS X shell with a visual display [NOT HEADLESS]
docker run -it \
    --device /dev/kvm \
    -p 50922:10022 \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -e "DISPLAY=${DISPLAY:-:0.0}" \
    -e GENERATE_UNIQUE=true \
    sickcodes/docker-osx:auto

# username is user
# passsword is alpine
```

Change password!