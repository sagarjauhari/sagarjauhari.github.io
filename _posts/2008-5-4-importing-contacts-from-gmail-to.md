---
title: Importing Contacts from Gmail to Thunderbird.
layout: post
category: code
tags: [ubuntu]
---

Initially, I exported the Gmail address book, in the .csv format and
tried to import the file in Thunderbird, but there was some problem. So,
incase, you are facing some difficulty, follow the alternate procedure:\

1.  Go to the contacts window in your Gmail acccount. Near the end you'd
    find the options export/import.
2.  Select the export option, and then, the v-card option.
3.  After the download, you'll have a contacts.vcf file probably.
4.  Login into your yahoo mail account (remember I told you: Alternate
    procedure !!). Go to contacts. Near the top, there'd be an option
    Export/Import. Import your file (the .vcf file mentioned above). It
    will notify that all xxx contacts successfully added. (I hope it
    does !! :) )\
5.  Now, again go back to export/import.\
6.  Now just below the place you clicked the 'import' button, there'd be
    an 'export' button with a few options, one of them saying 'for
    netscape and thunderbird (.ldif)'. Select that button, and Import
    the file. You will have a .ldif file where you saved it.
7.  Now, go to your Address book in thunderbird. Then to tools/import.
8.  Select the .ldif file. Press OK.
9.  That's it, all the fields 'd b matching correctly.\

PS: I know that this method is silly, but it worked very fast for me.
There's be methods far better and not so 'alternate', but this is also
one of the methids. And more importantly: IT WORKS !!
