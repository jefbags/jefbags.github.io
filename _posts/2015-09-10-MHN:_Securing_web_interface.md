---
layout: post
category: SEC
title: "MHN: Securing the web interface"
tagline: by jefbags
tags: 
 - security
 - MHN
 - honeypots
published: false 
---









<p />
## MHN: Securing the web interface

![pic]({{ site.baseurl }}/images/post7/pic1.png)


wiki pages:
https://github.com/threatstream/mhn/wiki/Running-MHN-Over-HTTPS

https://github.com/threatstream/mhn/wiki/MHN-Security


### creating keys:
https://help.ubuntu.com/lts/serverguide/certificates-and-security.html

sudo openssl genrsa -aes256 -out goya.lan.key.pem 2048

sudo chmod 400 goya.lan.key.pem

sudo openssl req -new -key goya.lan.key.pem -out goya.lan.csr.pem

sudo openssl x509 -req -days 1024 -in goya.lan.csr.pem -signkey goya.lan.key.pem -out goya.lan.crt.pem

sudo chmod 444 goya.lan.crt.pem


then followed instructions in MHN guide for HTTPS


then used ufw to stop connections via http


sudo ufw allow from 172.16.21.201 to any port 443

sudo ufw status

Because the scripts use wget, in the future, to deploy agents, it will be necessaary to add a temporary rule to enable the scripts to download

sudo ufw allow from 172.16.21.xxx to any port 80

or simply disable the ufw:

sudo ufw disable





In this post

<!--more-->

### Se
As



Installed following this excellent guide:
[https://itandsecuritystuffs.wordpress.com/2015/02/03/honeypot-networks/](https://itandsecuritystuffs.wordpress.com/2015/02/03/honeypot-networks/)




## Conclusion

