---
layout: post
category: SEC
title: "In the Land of Milk and Honeypots, part three"
tagline: by jefbags
tags: 
  - security
  - Linux
  - Ubuntu
published: true
---









<p />
## Let's set up the server...
<img align="right" src="{{ site.baseurl }}/images/linux.png">

As noted in my previous entries, I have been messing around with and documenting the creation of a honeypot server and environs, and the use of tools and techniques to analyze activity.  In the last post I set up the router using OpenWRT.   In this post, I will outline what was done to build the machine and setting up the base of the server environment.  

<!--more-->

## Cheap chips
The thing that is being reenforced as I move through this project is the ease and accessibility of the technology and software needed to complete it.  While Thomas Friedman might have proclaimed that the world is flat in his book a few years back, in no other place than information technology is the more evident and apparent.  There is so much readily availble electronics, and open source software, anyone can have in their hands almost immediately the tools they need.  Can you think of any other profession or hobby that is so instantaneously accessible?

Case in point, for this project I needed a separate, stand-alone device to throw to the wolves.  And, as previously documented, I am not interested in spending too much on this project.  But I know I need something with a little power behind it, otherwise what's the point?  Toward that end, I took this old computer that was in my basement, and designated it my DMZ device:

![pic]({{ site.baseurl }}/images/post4/pic2.png)

I yanked a bunch of critical pieces out of it, and put them in a box, like so... and then I replaced them with newer, cooler faster critical pieces.

![pic]({{ site.baseurl }}/images/post4/pic3.png)

And when's all said and done, I now have a more or less modern and beefy machine for some pretty short money.  
<img align="left" src="{{ site.baseurl }}/images/post4/pic4.png"> 
How many cores is that?  That's right, it's **8** bitches.  I am hoping that helps with processing on the virtual machines, along with enough RAM to make it look like I am trying to overcompensate for personal shortcomings. 

## Setting up the host server
For the OS, I decided to go with Ubuntu server.  I looked into Windows and a bunch of distro's but I really like Ubuntu.  It's powerful, yet friendly.  Even the error messages are pleasant and helpful.

![pic]({{ site.baseurl }}/images/post4/pic5.png) 

For packages and software, I kept it very simple. No GUI, no extra packages, no servers, limited services etc.  Actually, during the installation, when it asked me what I wanted to install, I think I only chose the SSH server, and host visualization tools.  I'll get into configuring them a little later.  I also want to harden the device, even more than the guest VM's, because this has got to last for the ages, while I imagine that the guests will be getting reset on a fairly regular basis.

### SSH keys
As with the router, will route most of the traffic through ssh, and secure authentication via keys.  I generated my keys elsewere and copied them onto the server using this nifty command:

	ssh-copy-id username@ip_address
    
### Other Hardening Stuff
I followed many of the instructions in this pretty good guide:  ( [_http://hardenubuntu.com/_](http://hardenubuntu.com/)), as well as sources, noted below.  Among some of things that were done:

I disabled the root account
	sudo passwd -l root

I disabled ipv6 for now

I upgraded openssl

I secured shared memory

I limited ssh access from the nat address of the router

I changed the ssh port

I secured the /tmp and /var/tmp folders

I removed unneeded services
 
I Disabled access to compilers (noting this here in case I need to go back and reenable these later...):

	sudo chmod 000 /usr/bin/byacc
	sudo chmod 000 /usr/bin/yacc
	sudo chmod 000 /usr/bin/bcc
	sudo chmod 000 /usr/bin/kgcc
	sudo chmod 000 /usr/bin/cc
	sudo chmod 000 /usr/bin/gcc
	sudo chmod 000 /usr/bin/*c++
	sudo chmod 000 /usr/bin/*g++

I Set alerts on login attempts

I Installed fail2ban

I Install PSAD Intrusion Detection


## Setting up email
One thing I wanted from this was email up and running so I can send alerts to myself.  I know that there To set up email, I decided to go with Postfix, and leverage Google for relaying.  I know that there are other options.  I guess could have used dynamic DNS, and set things up with my domain registration etc... but that is way more complicated than what I want to do for the purposes of this experiment.  Plus, you have to give Google credit for making this so easy and accessible.  There are tons on tutorials on how to set this on the Internet (I used this one: ( [_https://wiki.amahi.org/index.php/Gmail_As_Relay_On_Ubuntu_](https://wiki.amahi.org/index.php/Gmail_As_Relay_On_Ubuntu)).  Also, I made an account specifically for this purposes.

Although the setup went fine, I did have some issues with security worth mentioning.  When I tried to send a test message, I got this message from Google:

![pic]({{ site.baseurl }}/images/post4/pic6.png)

I reviewed the logs and noted the message:

	SASL authentication failed; server smtp.gmail.com... Please log in via your web browser and then try again.

The fix for this is to install an application specific password in Gmail.  It’s under *My Account* => *Sign-in & security* => *App passwords* (you need to have 2 step verification enabled).

Once done it’s necessary to edit /etc/postfix/sasl_passwd and update it with the newly generated application specific password.  The new password must be re-hashed:

	postmap /etc/postfix/sasl_passwd

Also, as good practice, ensure that the files /etc/postfix/sasl_passwd and /etc/postfix/sasl_passwd.db are accessible by root only by changing the ownership and permissions appropriately.  

http://hardenubuntu.com/server-setup/secure-shared-memory


### Virtually a server


## Conclusion
