---
layout: post
title: Java 调用默认浏览器打开指定网页
wordpress_id: 100
wordpress_url: http://www.hijava.org/?p=100
date: 2008-11-07 09:32:13.000000000 +08:00
---
以前介绍过<a href="http://www.hijava.org/j2se/open-a-webpage" target="_blank">Runtime.getRuntime().exec(cmdStr)</a>解决方式，现在发现这种解决方式不是很完美，不能打开<code>http://www.webspot.net.cn/?p=225这种类似的页面，而且只能用IEXPLORER打开。</code>

用google搜索了一下，找到了更完美的解决方法：
	java.net.URI uri=new java.net.URI("http://www.webspot.net.cn/?p=225");
	java.awt.Desktop.getDesktop().browse(uri);
