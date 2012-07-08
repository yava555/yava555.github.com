---
layout: post
title: 在线网页截图实现技术
wordpress_id: 673
wordpress_url: http://www.hijava.org/?p=673
date: 2010-04-20 19:26:46.000000000 +08:00
---
一直以来，就想做一个类似于<a href="http://www.websnapr.com/" target="_blank">websnapr</a>和<a href="http://www.superscreenshot.com/" target="_blank">Super Screenshot</a>这种提供网页截图服务的网站，今天对网页截图的关键技术进行了一些总结。

这里有篇文章：<a href="http://blog.csdn.net/cping1982/archive/2010/03/06/5353049.aspx" target="_blank">如何以Java实现网页截图技术</a>，介绍了实现网页截图的三种方式，使用Robot类、Jni调用第三方C/C++组件和自行解析。这三种方式对于我而言都不太合适，我又找到了另外一种实现方式，调用命令行程序，主要是找一些命令行网页截图工具，下面是我找到的一些工具，各有优缺：
<h3>IECapt</h3>
IECapt可以将捕获网页，生成BMP、JPEG 或 PNG格式的图片，包含C++和C#两种版本，不足是依赖于Internet Explorer，这就决定了它只能在Windows下使用。
	Usage: IECapt --url=http://www.hijava.org/ --out=localfile.png
参考链接： <a href="http://cutycapt.sourceforge.net/" target="_blank">http://cutycapt.sourceforge.net/</a>
<h3>CutyCapt</h3>
CutyCapt作为IECapt的兄弟，可以跨平台运行，生成的文件格式也多，SVG、PDF、 PS、 PNG、 JPEG,、TIFF,、GIF和BMP，CutyCap依赖于Qt。

Linux Shell下调用方式：
	% xvfb-run --server-args="-screen 0, 1024x768x24" ./CutyCapt --url=... --out=...
参考链接：
<ul>
	<li><a href="http://cutycapt.sourceforge.net/" target="_blank">http://cutycapt.sourceforge.net/</a></li>
	<li><a href="http://blog.saymoon.com/2009/11/take-snapshot-in-linux-command-line/" target="_blank">http://blog.saymoon.com/2009/11/take-snapshot-in-linux-command-line/</a></li>
</ul>
<h3>khtml2png</h3>
khtml2png是一种常用的命令行网页截图程序，不过需要安装庞大的KDE。
	Usage: khtml2png --width 1024 --height 768 --scaled-width 320 --scaled-height 240 http://www.hijava.org/ hijava.png
参考链接： <a href="http://khtml2png.sourceforge.net/" target="_blank">http://khtml2png.sourceforge.net/</a>
<h3>QtWebKit</h3>
	Usage: ./websnap www.hijava.org hijava.png
参考链接：
<ul>
	<li><a href="http://labs.trolltech.com/blogs/2009/01/15/capturing-web-pages/" target="_blank">http://labs.trolltech.com/blogs/2009/01/15/capturing-web-pages/</a></li>
	<li><a href="http://labs.trolltech.com/blogs/2008/11/03/thumbnail-preview-of-web-page/" target="_blank">http://labs.trolltech.com/blogs/2008/11/03/thumbnail-preview-of-web-page/</a></li>
	<li><a href="http://www.blogs.uni-osnabrueck.de/rotapken/2008/12/03/create-screenshots-of-a-web-page-using-python-and-qtwebkit/" target="_blank">http://www.blogs.uni-osnabrueck.de/rotapken/2008/12/03/create-screenshots-of-a-web-page-using-python-and-qtwebkit/</a></li>
</ul>
这些程序配置安装好后，就可以用高级语言调用命令行[Java中采用Runtime.getRuntime().exec(command)]，做一个在线网页截图的站点了。
