---
title: Configuring Thunderbird for Gmail.
layout: post
category: code
tags: [ubuntu]
---

Configuring Thunderbird in UBUNTU for downloading Gmail messages using
POP:\
Now , this was something that caused me a lot of trouble, and took me a
long time to start of with. But recently, I did work.\
\
The problem was that I was using the wrong information, and was baffled
when it was not working. Maybe the information worked in some onher
environments, but for me it was just the other side of what I needed.\
\
So, the configuration:(assuming that you have already installed
Thundebird, obviously)\
STEP 0:\
in your gmail account, go to settings/forwarding and pop/\
Select the radio button which enables POP access .\
\
STEP1:\
Download the latest Webmail and Webmail-Gmail plugins from the
internet.\
The link is: http://webmail.mozdev.org/installation.html\
[![](http://bp2.blogger.com/_w1ysKIz-K98/SB2jxjoZZGI/AAAAAAAAApY/qDxmuA3oSg8/s320/Screenshot-1.png)](http://bp2.blogger.com/_w1ysKIz-K98/SB2jxjoZZGI/AAAAAAAAApY/qDxmuA3oSg8/s1600-h/Screenshot-1.png)\
STEP 2:\
Open thunderbird, go to tools/addons. There will be an option: Install.
Click on that, and select your respective plugins (remember there are
two of them atleast).\
\
STEP 3:\
Restart thunderbird, and again go to tools/addons. You'd see your latest
installed plugins
there.[![](http://bp1.blogger.com/_w1ysKIz-K98/SB2jxToZZFI/AAAAAAAAApQ/Za8BjlDLnPM/s320/Screenshot.png)](http://bp1.blogger.com/_w1ysKIz-K98/SB2jxToZZFI/AAAAAAAAApQ/Za8BjlDLnPM/s1600-h/Screenshot.png)\
Click on the Webmail preferences. Edit it accordingly so that it looks
like this:\
[![](http://bp1.blogger.com/_w1ysKIz-K98/SB2n-ToZZHI/AAAAAAAAApg/wrd71XVz7O8/s320/Screenshot-WebMail+Options.png)](http://bp1.blogger.com/_w1ysKIz-K98/SB2n-ToZZHI/AAAAAAAAApg/wrd71XVz7O8/s1600-h/Screenshot-WebMail+Options.png)\
\
Note that the ports are all greater than 1024. Reason being that my
system, and some others block all ports below that. So, this is
important. On the internet you would often be asked to put ports like
995 or something, but they might not work.)\
\
STEP 4:\
Restart thunderbird and make sure that all the Servers show a green
ball, i.e. thy are all running. Now, go to edit/account settings/new
account/Gmail Account\
Fill in the information like this:\
[![](http://bp2.blogger.com/_w1ysKIz-K98/SB2n-joZZII/AAAAAAAAApo/Cwt8zIDxwfI/s320/Screenshot-Account+Settings.png)](http://bp2.blogger.com/_w1ysKIz-K98/SB2n-joZZII/AAAAAAAAApo/Cwt8zIDxwfI/s1600-h/Screenshot-Account+Settings.png)\
[![](http://bp3.blogger.com/_w1ysKIz-K98/SB2n-zoZZJI/AAAAAAAAApw/J09QiWTI4ww/s320/Screenshot-Account+Settings-1.png)](http://bp3.blogger.com/_w1ysKIz-K98/SB2n-zoZZJI/AAAAAAAAApw/J09QiWTI4ww/s1600-h/Screenshot-Account+Settings-1.png)\
\
Remember to put 'localhost' in the server box, and the respective server
port on shich the server is running (in step 3)\
\
STEP 5:\
for the SMTP server, fill in the information like this:\
[![](http://bp0.blogger.com/_w1ysKIz-K98/SB2n_DoZZKI/AAAAAAAAAp4/voWJgCkoygw/s320/Screenshot-Account+Settings-2.png)](http://bp0.blogger.com/_w1ysKIz-K98/SB2n_DoZZKI/AAAAAAAAAp4/voWJgCkoygw/s1600-h/Screenshot-Account+Settings-2.png)\
\
\
that's all, restart and it should downloading your gmail messages via
POP.\
\
any problems, leave comment.
