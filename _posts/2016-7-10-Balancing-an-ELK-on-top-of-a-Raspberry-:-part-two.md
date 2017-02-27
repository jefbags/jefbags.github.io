---
layout: post
category: SEC
title: "Balancing an ELK on top of a Raspberry, part two"
tagline: by jefbags
tags: 
 - security
 - Raspberry Pi
 - Suricata
 - OpenWRT
published: false
---









<p />
# Utilizing Suricata IDS and ELK to monitor network traffic

![pic]({{ site.baseurl }}/images/post8/pic1.png)

This is the second post related to setting up a home IDS system.  As previously The goal of this projects is to install intrusion detection monitoring and alerting on a home lab network using Raspberry Pi and ELK.  Last time we did basic set up.  This time we'll start sending traffic to Suricata and see how it can be parsed with Logstash, and visualized with Kibana.

Let's Begin!

<!--more-->

## Sending trafic to the IDS

Now that the system is up and running, and all the components are confiured, it's time to start sending traffic to the Raspberry Pi from the router.  To accomplish this, we'll be mirroring a port 

[http://donmizutani.com/pages/snort/setup/2-mirroring-network-traffic/](http://donmizutani.com/pages/snort/setup/2-mirroring-network-traffic/)

	opkg install iptables-mod-tee

	iptables -t mangle -A POSTROUTING -j TEE --gateway 192.168.1.202
	iptables -t mangle -A PREROUTING -j TEE --gateway 192.168.1.202

## Upgrading Kibana to version 4.5

It's Pretty easy really, make a copy of your current config file. this should be located at ..//config/kibana.yml, delete the kibana directory (rm -r /opt/kibana/), download the kibana 4.4 tar file and unzip into the same location as the previous kibana directory(rename base directories as needed). Replace the new kibana.yml file with the copied file from your previous installation. Make sure that you have elastic search 3.2 or greater.

##  Fixing the Tile Service and Visualizing

[https://www.elastic.co/blog/kibana-4-5-3-and-4-1-10](https://www.elastic.co/blog/kibana-4-5-3-and-4-1-10)

from mapquest
[http://devblog.mapquest.com/2016/06/15/modernization-of-mapquest-results-in-changes-to-open-tile-access/](http://devblog.mapquest.com/2016/06/15/modernization-of-mapquest-results-in-changes-to-open-tile-access/)

d






## Conclusion
The Raspberry Pi 
