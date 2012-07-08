---
layout: post
title: Google Translate API
wordpress_id: 470
wordpress_url: http://www.hijava.org/?p=470
date: 2009-08-15 14:49:18.000000000 +08:00
---
	http://ajax.googleapis.com/ajax/services/language/translate?
	q=hello%20world&langpair=en|zh-CN&v=1.0
q:要查询的字词
langpair=en|zh-CN:由英文翻译成中文，|竖线要转义为%7C
v=1.0:协议版本号

响应返回如下的JSON数据：
	{"responseData": {"translatedText":"世界您好"}, 
	"responseDetails": null, "responseStatus": 200}
一开始忘了指定langpair字段，结果折腾了半天，最后捕获了下灵格斯的数据包才得以解决。最近在学习Flex，打算利用Translate API做个adobe air应用。
