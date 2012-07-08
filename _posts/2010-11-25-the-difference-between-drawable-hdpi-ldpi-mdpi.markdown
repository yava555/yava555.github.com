---
layout: post
title: ! '[转]Android2.1中的 drawable(hdpi,ldpi,mdpi) 的区别'
wordpress_id: 990
wordpress_url: http://www.hijava.org/?p=990
date: 2010-11-25 18:36:49.000000000 +08:00
---
在之前的版本中，只有一个drawable，而2.1版本中有drawable-mdpi、drawable-ldpi、drawable-hdpi三个，这三个主要是为了支持多分辨率。

drawable- hdpi、drawable- mdpi、drawable-ldpi的区别：
<ol>
	<li>drawable-hdpi里面存放高分辨率的图片,如WVGA (480x800),FWVGA (480x854)</li>
	<li>drawable-mdpi里面存放中等分辨率的图片,如HVGA (320x480)</li>
	<li>drawable-ldpi里面存放低分辨率的图片,如QVGA (240x320)</li>
</ol>
系统会根据机器的分辨率来分别到这几个文件夹里面去找对应的图片。

在开发程序时为了兼容不同平台不同屏幕，建议各自文件夹根据需求均存放不同版本图片。

转自：<a href="http://blog.csdn.net/infsafe/archive/2010/03/29/5426562.aspx" target="_blank">http://blog.csdn.net/infsafe/archive/2010/03/29/5426562.aspx</a>
