---
title: Switching to ( or changing ) static IP address on Ubuntu Intrepid
layout: post
category: code
tags: [ubuntu]
---

Today, somehow the network of my college got reconfigured or something,
and all subnets got changed hostel wise. Hence, the network wasn't being
accessed by the old IP addresses. Now, in the earlier versions of Ubuntu
(before Intrepid) it was relatively easy to change the static IP
addresses from the Network Manager in the panel, but Intrepid onwards,
this intreface has been changed and I had been wondering for a while how
to do it. Now, today, since it was an absolutely desperate situation, I
finally figured a way out.

Solution:\

-   Open the file /etc/network/interfaces in your favourite editor:

\

You would find something like this:

\

***auto lo\
iface lo inet loopback***

\

***\
iface eth0 inet static\
address 10.4.1.41\
netmask 255.0.0.0\
auto eth0\
***

\

\

-   If you don't find the last 4 lines in this file, then your network
    configuration is set to dynamic IP. So, add these four lines to the
    end of this file. And, if your see these lines, it means your have
    previously set your IP address to static. Now, to change your static
    adderss, change the address given below the line 'iface eth0 static'
    (here, 10.4.1.41)to whatever address u want.

-   Finally, restart the networking service by the command:

-   Verify the change by the command:

\$ip addr\
\
You would see the new IP address in the eth0 section!\

\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\~\

Now, I stumbled upon this solution when I was checking out the man pages
of 'ip' and related commands and then I tried the command for restarting
the network. When it didn't work, I opened the file
/etc/init.d/networking and found that that the script uses the files in
the /etc/network directory. There I found the file named 'interfaces'
and upon opening it, I knew this was what I was searching for!
