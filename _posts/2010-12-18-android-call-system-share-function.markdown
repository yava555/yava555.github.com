---
layout: post
title: Android分享功能
wordpress_id: 1036
wordpress_url: http://www.hijava.org/?p=1036
date: 2010-12-18 18:57:15.000000000 +08:00
---
代码如下：
	Intent intent=new Intent(Intent.ACTION_SEND);
	intent.setType("text/plain");
	intent.putExtra(Intent.EXTRA_SUBJECT, "分享");
	intent.putExtra(Intent.EXTRA_TEXT,"I would like to share this with you...");
	startActivity(Intent.createChooser(intent, getTitle()));

