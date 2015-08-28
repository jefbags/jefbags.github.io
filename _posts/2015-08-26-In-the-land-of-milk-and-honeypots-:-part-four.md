---
layout: post
category: SEC
title: "In the Land of Milk and Honeypots, part four"
tagline: by jefbags
tags: 
 - security
 - virtualization
 - Ubuntu
published: false
---









<p />
## Virtually a server...

![pic]({{ site.baseurl }}/images/post5/pic3.png)

As noted in my previous entries, I have been messing around with and documenting the creation of a honeypot server and environs, and the use of tools and techniques to analyze activity. In the last post I set up the router using OpenWRT. In this post, I will outline what was done to build the machine and setting up the base of the server environment. 

<!--more-->

## Testing open ports

Checking for open ports:
nmap -v -sT localhost
sudo nmap -v -sS localhost


Checking for open relay:
https://www.safaribooksonline.com/library/view/nmap-6-network/9781849517485/ch06s03.html
https://scottlinux.com/2015/06/15/use-nmap-to-test-for-open-mail-relay/


## Making backups

http://hardenubuntu.com/backup/

## Starting up with KVM
Using KVM via the command line requires a little bit more setup than I am used to.  As with other facets of 

To install the guest virtual machine, I opted to go with virt-install rather than the virt manager, or 

	sudo apt-get virtinst

	sudo mount -t iso9660 /dev/dvd /media/cdrom/

	sudo dd if=/dev/dvd of=dvd.iso

	
this one:

sudo virt-install --connect qemu:///system -n vivid_template -r 6144 --vcpus=2 --disk path=/disk2/kvm/images/vividTemplate.img,size=400 --location=/media/cdrom --graphics none --os-type linux --description "Template Ubuntu Vivid Guest" --network=bridge:virbr0 --extra-args='console=tty0 console=ttyS0,115200n8 serial'

Didn't work due to X11 issues!

Had issues with SSH, had to enable following in server sshd_config

	X11UseLocalHost no

And also had to make sure that following was uncommented in my local ssh

	ForwardX11Trusted yes

Installed Virtualbox:

	apt-get install virtualbox

run with 

	virtualbox &

Set up.

Start via command line:

	sudo VBoxManage startvm "VM name" --type headless

chnaged:

/etc/hosts
/etc/hostname

$home/.bash_profile
/etc/psad/psad.conf
/etc/postfix/main.cf


sudo dump 0zf /backups/bosch.boot.backup.8.27.2015 /boot
sudo dump 0zf /backups/bosch.root.backup.8.27.2015 /

sudo dump 0zf /backups/vermeer.boot.backup.8.27.2015 /boot
sudo dump 0zf /backups/vermeer.root.backup.8.27.2015 /

changed ICMP rules on host (/etc/ufw/rules.before)
# ok icmp codes for INPUT
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP



## Conclusion