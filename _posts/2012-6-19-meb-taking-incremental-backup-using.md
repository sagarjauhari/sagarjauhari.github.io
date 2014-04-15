---
title: MEB - Taking Incremental Backup using last successful backup
layout: post
category: code
tags: [meb mysql enterprise backup mysql backup oracle incremental]
---

Published another post on MySQL Enterprise Backup at Oracle blogs
today.\

> \
> A new prefix
> '[history:'](http://dev.mysql.com/doc/mysql-enterprise-backup/3.7/en/backup-incremental-options.html#option_meb_incremental-base) has
> been introduced for the –incremental-base option and currently the
> only permissible value is the string "last\_backup". So using the new
> option an incremental backup can be taken with the following command:\
> `$ mysqlbackup --incremental --incremental-backup-dir=/media/mysqlbackup-repo/ --incremental-base=history:last_backup backup`

Read more here: <https://blogs.oracle.com/MySQL/entry/meb> \

