---
layout: post
title: Linux下的计划任务Crontab
wordpress_id: 660
wordpress_url: http://www.hijava.org/?p=660
date: 2010-04-10 15:20:04.000000000 +08:00
---
<blockquote>crontab命令常见于Unix和类Unix的操作系统之中，用于设置周期性被执行的指令。该命令从标准输入设备读取指令，并将其存放于“crontab”文件中，以供之后读取和执行。该词来源于希腊语 chronos(χρόνος)，原意是时间。</blockquote>
<h3>1、查看系统中已经执行的计划任务：</h3>
	crontab -l
<h3>2、编辑计划任务：</h3>
	crontab -e
使用 crontab 命令和 -e（表示 “edit”）选项创建 crontab。这会打开 vi  编辑器，除非在 EDITOR 或 VISUAL 环境变量中指定了另一种编辑器。
<h3>3、文件格式说明：</h3>
	#——分钟 (0 - 59)
	# |——小时 (0 - 23)
	# | |——日   (1 - 31)
	# | | |——月   (1 - 12)
	# | | | |——星期 (0 - 7)（星期日=0或7）
	# | | | | |
	# * * * * * 被执行的命令
<h3>4、常用例子：</h3>
每隔5分钟执行一次
	*/5 * * * *  /home/user/test.pl
周一到周五凌晨1点执行
	0 1 * * 1-5 /home/user/test.pl
更多解释：<a href="http://en.wikipedia.org/wiki/Crontab" target="_blank">http://en.wikipedia.org/wiki/Crontab</a>
