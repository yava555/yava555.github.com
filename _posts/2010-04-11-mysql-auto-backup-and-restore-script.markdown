---
layout: post
title: Mysql自动备份和还原脚本
wordpress_id: 665
wordpress_url: http://www.hijava.org/?p=665
date: 2010-04-11 15:54:20.000000000 +08:00
---
工作的时候写得一个脚本，可以自动备份Mysql远程数据库数据，并还原到本地。
	@echo off
	set remote_host=192.168.1.7
	set remote_db=dbname
	set romote_user=username
	set remote_passwd=passwd
	set local_db=dbname
	set local_user=username
	set local_passwd=passwd
	echo '备份远程数据库数据'
	mysqldump -h%remote_host% -u%romote_user% -p%remote_passwd% --skip-lock-tables --default-character-set=utf8 %remote_db%> pm.sql
	echo '恢复本地数据库数据'
	mysql -u%local_user% -p%local_passwd% --default-character-set=utf8 %local_db%< pm.sql
	pause

