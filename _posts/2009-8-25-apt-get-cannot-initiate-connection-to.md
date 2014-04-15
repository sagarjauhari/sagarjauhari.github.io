---
title: Apt-get- Cannot initiate the connection to 8080:80 (0.0.31.144).
layout: post
category: code
tags: [bash apt-get /etc/apt/conf]
---

I've seen this problem sometimes cropping up! One of the reasons this
problem can occur is when your http\_proxy variable is not set
properly!\
The \$http\_proxy variable in your terminal overrides the http::proxy
variable in /etc/apt/conf file and the connection is not established if
the http\_proxy variable in the terminal is set to [proxy]:[port]
instead of http://[proxy]:[port]. To check this out do the following:\

1.  Type: echo \$http\_proxy in the terminal
2.  If it is something like this: 10.1.1.30:8080, then type:
    http\_proxy="http://10.1.1.30:8080" . (we're just adding the
    'http://' before the content of the variable)

If the problem was because of the overriding variables, it'd be solved
by now .. try typing sudo apt-get update and see if it works.
