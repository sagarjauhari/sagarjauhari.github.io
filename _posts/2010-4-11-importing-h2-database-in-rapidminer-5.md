---
title: Importing H2 database in RapidMiner 5
layout: post
category: code
tags: []
---

Hi! Here's the configuration to import your H2 database in Rapidminer:\
 \
 \
 \

[![](http://4.bp.blogspot.com/_w1ysKIz-K98/S8GjYwbBrUI/AAAAAAAACbI/aaX4AXKtuLo/s320/1.png)](http://4.bp.blogspot.com/_w1ysKIz-K98/S8GjYwbBrUI/AAAAAAAACbI/aaX4AXKtuLo/s1600/1.png)

1.  **Add the H2 driver to RapidMiner:** Go to 'Manage Database Drivres'
    and configure it is follows: (The Jar file lies in the /bin folder
    of your H2 installation; give its path). Save these settings\
     \
     \
     \
     \
     \
     \
     \
     \
     \
     \
2.  Now go to your process window in RapidMiner and drag the
    'ReadDatabase' operator:

[![](http://4.bp.blogspot.com/_w1ysKIz-K98/S8GlDOrABmI/AAAAAAAACbY/4sdfjPgwi2k/s320/3.PNG)](http://4.bp.blogspot.com/_w1ysKIz-K98/S8GlDOrABmI/AAAAAAAACbY/4sdfjPgwi2k/s1600/3.PNG)

\

[![](http://3.bp.blogspot.com/_w1ysKIz-K98/S8Gm9PJLbFI/AAAAAAAACbo/RD1Q3Ow5msY/s320/4.PNG)](http://3.bp.blogspot.com/_w1ysKIz-K98/S8Gm9PJLbFI/AAAAAAAACbo/RD1Q3Ow5msY/s1600/4.PNG)3.
Click on it and add attribute values as shown in the image:\
 (database url is the complete url of your embedded database file). The
default username in H2 is 'sa' without password. But, this won't work
for RapidMiner since its mandatory to give some password. So, Create a
new user with some password using the 'CREATE USER' sql command. In my
case, I created a new database user called 'user1'.\
 \
 4. Once this is done, restart RapidMiner for changes to take place. Do
not forget to save your process when RapidMiner prompts you to.\
 \

[![](http://4.bp.blogspot.com/_w1ysKIz-K98/S8Gnr5AVa6I/AAAAAAAACbw/Mio79uFtC0E/s320/5.PNG)](http://4.bp.blogspot.com/_w1ysKIz-K98/S8Gnr5AVa6I/AAAAAAAACbw/Mio79uFtC0E/s1600/5.PNG)5.
Now, Click on Build SQL Query. You'll see something like what is shown
on left. Select the table you want to read (just click on the name of
the table and the select \* query will be generated) and click OK\
 \

