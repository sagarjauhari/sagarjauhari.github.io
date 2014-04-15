---
title: Disabling remote access to phpmyadmin
layout: post
category: code
tags: [ubuntu]
---

I installed the LAMP + phpmyadmin combo yesterday on my Ubuntu Intrepid
machine for hosting a local website.\
But later I realized that the phpmyadmin page, though password
protected, was visible throughout my local network! So, to disable
remote access to phpmyadmin , add the following code to the end of your
/etc/apache2/apache2.conf file ..\
\
\
\# Disabling phpmyadmin for remote access\
\<directory\>\
Order Deny,Allow\
Deny from all\
Allow from localhost\
\</directory\>
