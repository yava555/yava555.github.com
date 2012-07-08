---
layout: post
title: 用Robot类来实现屏幕截图
wordpress_id: 165
wordpress_url: http://www.hijava.org/?p=165
date: 2009-02-16 19:01:38.000000000 +08:00
---
今天浏览网页的时候，偶然发现了java.awt.Robot这个类，用它可以实现屏幕截图。关键代码如下：
	Robot robot=new Robot();
	BufferedImage buffImage=robot.createScreenCapture(new Rectangle(Toolkit.getDefaultToolkit().getScreenSize()));
	ImageIO.write(buffImage, "jpg", new File("test.jpg"));
进一步扩展，可以实现远程电脑屏幕监控。

原文：<a href="http://www.blogjava.net/wang9354/archive/2009/02/12/254437.html" target="_blank">http://www.blogjava.net/wang9354/archive/2009/02/12/254437.html</a>
