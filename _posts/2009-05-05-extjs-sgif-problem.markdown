---
layout: post
title: ExtJS s.gif问题
wordpress_id: 361
wordpress_url: http://www.hijava.org/?p=361
date: 2009-05-05 17:18:12.000000000 +08:00
---
用调试ExtJS的时候，会发现浏览器总会去ExtJS官网去请求s.gif文件，具体URL是：http://extjs.com/s.gif  如果连接不上ExtJS.com网站界面就会出现显示问题。解决这个问题很简单：在执行Ext.onReady()方法之前，执行下面这行代码就可以了。
	Ext.BLANK_IMAGE_URL = "extjs/resources/images/default/s.gif";
