---
title: C:/Windows/Installer directory overflowing bug?
layout: post
category: code
tags: []
---

DISCLAIMER: I accept no liability for the content of this post, or for
the consequences of any actions taken on the basis of the information
provided. Use this solution at your own risk. This is a solution which
worked on my system and may / may not work on others.\
 \
 Hi all. Recently was bugged by the problem of my C: getting used up
erratically. Everyday i'd remove some application and free space and lo!
Next morning again \<20MB space left on this drive.\
 I used the following tool to figure out the problem:\
 Free Disk Analyzer from <http://www.extensoft.com/>\
 Saw that the folder C:/Windows/Installer took up almost 80% of the
space!\
[![](http://4.bp.blogspot.com/_w1ysKIz-K98/TKwDtG3w3DI/AAAAAAAACtA/w69cX4rdzI8/s320/CropperCapture%5B6%5D.jpg)](http://4.bp.blogspot.com/_w1ysKIz-K98/TKwDtG3w3DI/AAAAAAAACtA/w69cX4rdzI8/s1600/CropperCapture%5B6%5D.jpg)
Initially thought of deleting several files at random but then read in
forums that this approach is definitely not advisable. In many forums I
was redirected to this
page: <http://support.microsoft.com/default.aspx?scid=kb;en-us;290301> but
as it says, they've removed the installer from here.  This utility,
however, can still be download
from <http://majorgeeks.com/Windows_Installer_CleanUp_Utility_d4459.html>.
INSTALL IT. Do not go and run this utility from its GUI since it doesn't
give the option of removing only 'orphaned' installer packages - which
is what we want to do. So, fire your command prompt, cd to C:\\Program
Files\\Windows Installer Clean Up and run : **msizap g!**\
 **\
**\
 PS: Cleaned up 16GB of space in 10 sec!
