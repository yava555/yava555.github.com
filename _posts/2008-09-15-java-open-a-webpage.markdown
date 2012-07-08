---
layout: post
title: Java如何打开网页链接
wordpress_id: 62
wordpress_url: http://www.hijava.org/?p=62
date: 2008-09-15 13:21:59.000000000 +08:00
---
可以通过Runtime类调用执行explorer命令打开网页，示例代码如下：
	String cmdStr = "explorer http://www.hijava.org/";
	try {
		Runtime.getRuntime().exec(cmdStr);
	} catch (IOException e) {
		e.printStackTrace();
	}
不过这种解决方式并不是很完美，不能打开带参数的页面（例如：<em>http://www.hijava.org/?p=32</em>），而且只会调用 IE打开网页。

用google搜索了一下，找到了更完美的解决方法：
	java.net.URI uri=new java.net.URI("http://www.hijava.org/?p=32");
	java.awt.Desktop.getDesktop().browse(uri);
