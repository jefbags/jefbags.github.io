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

Case in point, for this project I needed a separate, stand-alone device to throw to the wolves.  And, as previously documented, I am not interested in spending too much on this project.  But I know I need something with a little power behind it, otherwise what's the point?  Toward that end, I toook this old computer that was in my basement, and designated it my DMZ device:

![pic]({{ site.baseurl }}/images/post4/pic2.png)

I yanked a bunch of critical pieces out of it, and put them in a box, like so... and then I replaces them with newer, cooler faster critical pieces.

![pic]({{ site.baseurl }}/images/post4/pic3.png)

And when's all said and done, I now have a more or less modern and beefy machine for some pretty short money.  

PIC

How many cores is that?  That's right, it's 8 bitches.  I am hoping that helps with processing on the virtual machines, along with enough RAM to make it look like I am trying to overcompensate for personal shortcomings. 

## Setting up the host server
For the OS, I decided to go with Ubuntu server.  I looked into Windows and a bunch of distro's but I really like Ubuntu.  It's powerful, yet friendly.  Even the error messages are pleasant and helpful.

PIC 

For packages and software, I kept it very simple. No GUI, no extra packages, no servers, limited services etc.  Actually, during the installation, when it asked me what I wanted to install, I only chose the SSH server, and host virtualization tools.  I'll get into configuring them a little later.  I also want to harden the device, even more than the guest VM's, because this has got to last for the ages, while I imagine that the guests will be getting reset on a fairly regular basis.

### SSH keys

### Other Hardening Stuff

### Virtually a server


## Conclusion


