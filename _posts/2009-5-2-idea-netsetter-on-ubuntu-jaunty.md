---
title: Idea Netsetter on Ubuntu Jaunty Jackalope - Step by step procedure
layout: post
category: code
tags: [ppp0 internet idea netsetter wvdial ubuntu]
---

It took some time but I managed to configure the Idea Netsetter wireless
USB plug and surf device on my Ubuntu laptop. It wasn't as tough as I
had thought. Here's the procedure:\
\
Step 1. Write the following in your /etc/wvdial.conf file, save and
close:\
\
\
[Dialer Defaults]\
Modem=/dev/ttyUSB0\
Baud = 460800\
Init 1 = AT+CGMM\
Init 2 = AT+CMEE=1\
Init 3 = ATE0\
Init 4 = AT\^HS=0,0\
Init 5 = AT+CFUN?\
Init 6 = AT+CLCK="SC",2\
Init 7 = AT+CPIN?\
Init 8 = AT+CLCK="SC",2\
Modem Type = USB MODEM\
Phone=\*99\#\
Username = idea\
Password = idea\
Dial Command=ATDT\
Stupid Mode=1\
ISDN=0\
APN = internet\
\
\
Step 2. Add the following lines to your /etc/network/interfaces file:\
\
iface ppp0 inet ppp\
provider ppp0\
auto ppp0\
\
It would look something like this (only the encircled part is
important):\
\
\
[![](http://4.bp.blogspot.com/_w1ysKIz-K98/SfxInMhJUwI/AAAAAAAACG0/u8XZp2THfqs/s320/Screenshot.png)](http://4.bp.blogspot.com/_w1ysKIz-K98/SfxInMhJUwI/AAAAAAAACG0/u8XZp2THfqs/s1600-h/Screenshot.png)\
\
Step 3. Restart the network services by the following command:\
\
 \$ sudo /etc/init.d/networking restart\
\
Step 4. Go to System-\> Administration -\> Network. You'd see something
like this:\
[![](http://1.bp.blogspot.com/_w1ysKIz-K98/SfxGkCMaedI/AAAAAAAACGs/mMXUay8O4rk/s400/Screenshot-Network+Settings.png)](http://1.bp.blogspot.com/_w1ysKIz-K98/SfxGkCMaedI/AAAAAAAACGs/mMXUay8O4rk/s1600-h/Screenshot-Network+Settings.png)\
Uncheck the 'Wired' connection (disable it). Now go to the properties of
Point to point connection do the following settings in the respective
tabs:\
\
[GENERAL]:\

-   Check on 'Enable this connection'
-   Connection type: PPPoE
-   Username: idea
-   password: idea

[MODEM]:\

-   Ethernet interface: eth0

[OPTIONS]\

-   Check 'Set modem as default'
-   Check 'Use the internet service provider nameservers'
-   Check 'Retry if connection breaks'

\
Step 5. Again restart the network connection (step 3).\
\
Step 6. Plug in your Idea Netsetter in one of the USB ports and run the
following command in your terminal:\
\
\$ sudo wvdial\
\
\
That's it .. if everything's fine wvdial would show your new Local and
Remote IP address for the idea connection.\
\
Have fun.
