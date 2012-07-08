---
layout: post
title: ubuntu下安装JDK
wordpress_id: 516
wordpress_url: http://www.hijava.org/?p=516
date: 2009-11-08 20:30:12.000000000 +08:00
---
1、从java.sun.com下载JDK，我下载的是jdk-6u17-linux-i586.bin ，执行命令添加执行权限。

	sudo chmod 777 jdk-6u17-linux-i586.bin

2、执行命令，安装JDK。

	./jdk-6u17-linux-i586.bin

3、修改/etc/environment文件，设置系统环境变量。

	sudo gedit c/etc/environment

加入如下部分内容：

	JAVA_HOME="/home/yava/jdk1.6.0_17"
	PATH="..........:/home/yava/jdk1.6.0_17/bin"
	CLASSPATH=".:/home/yava/jdk1.6.0_17/lib"

4、重启系统
