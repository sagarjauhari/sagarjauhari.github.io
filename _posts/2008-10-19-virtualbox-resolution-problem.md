---
title: Virtualbox resolution problem
layout: post
category: code
tags: [ubuntu]
---

Problem: Guest machine doesn't switch to full screen even after
installing VBox additions.\
\
One possible solution:\
Switch to seamless mode (host key + L ), and then back to full screen
mode. !!\
\
\
\
I run Windows XP on Ubuntu using Virtualbox, and recently came across
this resolution problem: my notebook resolution is 1280X800 and in the
virtual machine, it was just not allowing me to set the resolution to
this ! Most people asked me to install VBox additions but I had already
installed them... others asked me to increase the video memory of the
virtual machine to 20 MB because that gave more options for
resolution... even then, all other resolution options were there except
1280X800 !!\
\
It was really annoying to have some other resolution and as a last
resort, i thought of using the seamless mode (host+L). It was cool, but
I had to switch off the compiz effects. Then, i tried the full screen
mode again..... and guess what.... the screen resolution was
automatically set to 1280X800 !!!
