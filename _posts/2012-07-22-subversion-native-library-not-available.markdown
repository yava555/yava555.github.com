---
layout: post
title: Subversion Native Library Not Available
date: 2012-07-22 10:35:22.000000000 +08:00
categories:
- 技术
tags:
- eclipse
- subclipse
- svn

---

在Mac OS X系统下使用eclipse的subclipse插件时报了如下错误：  

`Failed to load JavaHL Library.
These are the errors that were encountered:
no libsvnjavahl-1 in java.library.path
no svnjavahl-1 in java.library.path
no svnjavahl in java.library.path
java.library.path = .:/Library/Java/Extensions:/System/Library/Java/Extensions:/usr/lib/java`

解决方式十分简单，安装JavaHL即可：

	sudo port install subversion-javahlbindings
	
参照链接：[在Mac OS X上安装JavaHL](http://www.khotyn.com/2011/01/09/%E5%9C%A8mac-os-x%E4%B8%8A%E5%AE%89%E8%A3%85javahl/)