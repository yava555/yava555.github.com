---
layout: post
title: ExtJs 对象不支持此属性或方法
wordpress_id: 354
wordpress_url: http://www.hijava.org/?p=354
date: 2009-05-04 17:40:23.000000000 +08:00
---
用IE浏览器打开ExtJs项目时报得一个错误：“对象不支持此属性或方法”，“var range = el.ownerDocument.createRange();”，解决方式非常简单，给body内出现的第一个元素加上标签即可。

This is an issue in IE where the first element of the body can't be a text node.
body标签内的第一个元素不能为文本text，否则IE浏览器会报错
