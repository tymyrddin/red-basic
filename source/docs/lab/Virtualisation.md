# Small lab with virtualisation

Create a testlab with:

* A Kali machine: The Kali machine serves as attack machine, as development machine for hacking-related scripts, and for using its apache2 webserver to serve hooks and files.
* One or two Windows machines, both 10 or a 10 and an 11 machine: One of the two serves as development machine for scripts that are best developed on the target (with defenses turned off) they are meant for. This machine will need Python installed on it. The second one, if created, can be used to test binaries, and does not need to have Python installed.
* A Metaspoit machine: The metasploit provides targets for the most simple attacks.

If you do not have virtualisation, you can set up a lab with a few old buckets. If the machine you are on supports virtualisation, you can use VMWare and ready-made guests, or use KVM and make the virtual machines yourself. Do not run both virtualisation solutions, or turn off one in `systemctl` when using the other. Switching is a hassle though.

In all cases you can use testing versions from Microsoft (for 90 days) for the Windows 10 VM. In virtualized machines make a snapshot immediately after install, to return to when time runs out.

## Using VMWare 
* [Microsoft test VM's](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/) - 90 days
* [Official Kali VM's](https://www.kali.org/get-kali/#kali-virtual-machines)
* [ZSecurity kali linux VM](https://zsecurity.org/download-custom-kali/) - set it to 4G RAM
* [Metasploitable](https://information.rapid7.com/metasploitable-download.html)

## Using KVM
* [Windows 10 enterprise edition iso](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise) - 90 days
* [Windows 10 Home or Pro iso](https://www.microsoft.com/en-in/software-download/windows10ISO) - 90 days
* [Kali iso](https://www.kali.org/get-kali/#kali-bare-metal)
* [Metasploitable](https://information.rapid7.com/metasploitable-download.html) - Import the `.kvmd`

#### How to
* [How To Install Windows 10 on Ubuntu KVM?](https://getlabsdone.com/install-windows-10-on-ubuntu-kvm/)
* [Hosting a Kali Linux virtual machine using KVM on an Ubuntu 20.10 box](https://heds.nz/posts/hosting-kali-linux-kvm-ubuntu/)