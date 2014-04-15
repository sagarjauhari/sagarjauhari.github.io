---
title: JAVA Swing and AWT applications freezing in Ubuntu
layout: post
category: code
tags: [ubuntu]
---

Now I had been facing this problem from quite some time, but recently
found a quick solution. Well, by default, the system uses GIJ as the
Java byte interpretor and possibly, it causes the applications to
freeze. I had installed the sun-java-6 jdk package but it was not
functional because gij was the default one.\
\
Steps:\
\
1. Install the sun-java6-sdk package.\
2. Find the default jvm being used by your machine by typing: java
-version\
3. In case it shows 'gij', then type: sudo update-alternatives --config
java\
It would list all the possible options with a number corresponding to
each. For me it shows:\
\
There are 5 alternatives which provide \`java'.\
\
Selection Alternative\
-----------------------------------------------\
 1 /usr/bin/cacao\
\* 2 /usr/lib/jvm/java-6-sun/jre/bin/java\
 3 /usr/lib/jvm/java-1.5.0-sun/jre/bin/java\
 4 /usr/bin/gij-4.3\
+ 5 /usr/lib/jvm/java-gcj/jre/bin/java\
\
Press enter to keep the default[\*], or type selection number:\
\
4. Type in the corresponding number to java-6-sun/jre/bin/java, and
press return.\
\
\
That's all... unsure the version of java again by typing th command in
step 2, hopefully you will see something different :)
