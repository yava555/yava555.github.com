---
layout: post
title: Extjs DateField在firefox下显示过长的问题
wordpress_id: 392
wordpress_url: http://www.hijava.org/?p=392
date: 2009-05-16 16:46:11.000000000 +08:00
---
在页面中加入如下CSS代码即可：
	.x-date-middle {
	  padding-top:2px;padding-bottom:2px;
	  width:130px; /* FF3 */
	}
