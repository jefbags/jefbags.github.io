---
layout: post
category: SEC
title: "In the Land of Milk and Honeypots, part two"
tagline: by jefbags
tags: 
  - security
  - OpenWRT
  - networking
published: false
---



<p />
# Setting the stage...

As noted in my previous entry, the purpose of this series of posts is to document the creation of a honeypot, and the use of tools and techniques to analyze activity.  In this post, I will continue configuring the OpenWRT router, lock down some of the settings, and also set up some NAT's and open ports.
<!--more-->

## Installing tcpdump

First things first, we have to lock down the LinkSys router.  To that, we will lock it down.  Before we begin, there’s something I want to add to the router.  It’s one of the best, simple networking tools in the world:  tcpdump.  I want this because I am going to use it to test the natted IP's that are created later on.

To get started, first go to update the package list on the device:

	opkg update

Then install the package

	opkg install tcpdump

Ok, so that was slow.  This router is struggling.  Will probably look into upgrading later on.  There is barely enough memory or space on this thing to do a lot.

![pic]({{ site.baseurl }}/images/post2/pic1.png)

To test that the tool is installed ok, I'll monitor the LAN interface for ICMP traffic, and ping it:

	tcpdump -i br-lan icmp

Ok, seems to be up and running!  REbooted a few times, and retested.  We are set to move on.

![pic]({{ site.baseurl }}/images/post2/pic2.png)

## Hardening the OpenWRT device

Next I need to lock the router down.  There are several standard steps that will be taken.  Mostly, I following along with the items noted on the OpenWRT website where an excellent tutorial exists ([http://wiki.openwrt.org/doc/howto/secure.access](http://wiki.openwrt.org/doc/howto/secure.access)).



> test


	test2
    test2







![pic1]({{ site.baseurl }}/images/post1/pic1.png)

I wanted to be able to access my test device out on the DMZ network.  To do this, I set up a rule opening up port 5900 to the LAN.

# 1.  Open up ports to LAN/WAN
Dd

# 2.  Set up virtual server

# 3.  Set up honeypot server

# 4.  Set up tcpdump (POC)

# 5.  s

-	Set up Honeypot server
-	Logging/Monitoring/Alerting on specific actions and intrusions
-	Database of origins of actions
-	Experiment with scanning attackers back



 



## Conclusion
