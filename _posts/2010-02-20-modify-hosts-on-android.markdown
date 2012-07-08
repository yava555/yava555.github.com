---
layout: post
title: Android 修改Hosts文件
wordpress_id: 538
wordpress_url: http://www.hijava.org/?p=538
date: 2010-02-20 23:11:14.000000000 +08:00
---

	$su
	#mount -o remount,rw -t yaffs2 /dev/block/mtdblock3 /system
	echo "168.143.161.20 twitter.com www.twitter.com" >> /etc/hosts
	mount -o remount,ro -t yaffs2 /dev/block/mtdblock3 /system

