---
title: How to fix the No Sound problem in Ubuntu 8.10 (Intrepid)
layout: post
category: code
tags: [ubuntu]
---

You might have come across the 'no sound' problem after a fresh
installation of Ubuntu 8.10 Intrepid. Well, there are a couple of
solutions around and this one worked for me :\
\
1. Go to System -\> Administration -\> Users and Groups\
[![](http://4.bp.blogspot.com/_w1ysKIz-K98/SRNXuZvh5ZI/AAAAAAAABP4/GudqOHgYU1g/s400/Screenshot-Users+Settings.png)](http://4.bp.blogspot.com/_w1ysKIz-K98/SRNXuZvh5ZI/AAAAAAAABP4/GudqOHgYU1g/s1600-h/Screenshot-Users+Settings.png)\
\
\
2. Click on 'Unlock' and enter password.\
3. Next, go to 'Manage Groups'.\
4. Search for the groups 'pulse' and 'pulse access'\
[![](http://1.bp.blogspot.com/_w1ysKIz-K98/SRNXuMS7iLI/AAAAAAAABPw/OIVLQ-bYIjk/s400/Screenshot-Groups+settings.png)](http://1.bp.blogspot.com/_w1ysKIz-K98/SRNXuMS7iLI/AAAAAAAABPw/OIVLQ-bYIjk/s1600-h/Screenshot-Groups+settings.png)\
\
\
5. For both of these, double click on them and add yourself to this
group by checking on the check-box.\
[![](http://4.bp.blogspot.com/_w1ysKIz-K98/SRNXuH6WnnI/AAAAAAAABPo/giFUOmlP5QQ/s400/Screenshot-Group+%27pulse%27+Properties.png)](http://4.bp.blogspot.com/_w1ysKIz-K98/SRNXuH6WnnI/AAAAAAAABPo/giFUOmlP5QQ/s1600-h/Screenshot-Group+%27pulse%27+Properties.png)\
\
6. Hopefully, you are done !! Logout with ctrl+alt+backspace, and login
again.
