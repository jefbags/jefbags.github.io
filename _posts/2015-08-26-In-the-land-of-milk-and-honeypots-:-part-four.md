---
layout: post
category: SEC
title: "In the Land of Milk and Honeypots, part four"
tagline: by jefbags
tags: 
 - security
 - Linux
 - Ubuntu
published: false
---









<p />
## Virtually a server...
<img align="right" src="{{ site.baseurl }}/images/linux.png">

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
The th




## Conclusion