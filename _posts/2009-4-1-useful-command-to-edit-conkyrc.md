---
title: Useful command to edit .conkyrc
layout: post
category: code
tags: [ubuntu conky]
---

Friends this is a simple command I use whenever I edit my conkyrc file:\
\
\$while true; do conky -q -i 10; sleep 3; done\
\
Starting conky this way kills it and restarts it after every 3+10\*n
seconds, where n is the update interval mentioned in your conkyrc file.
So, you can open \~/.conkyrc file in your editor run the above command.
You would see the changes on the conky right on your desktop as it is
restarted again and again. (please dont forget to keep saving the file
as you edit it to make this thing work).\
\
By the way, I have edited a conkyrc file i found on a webiste and
finetuned it !! My conky is simply amazing now :) I'd post the file in
my next post (and a snapshot of my desktop).
