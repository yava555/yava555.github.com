---
layout: post
title: ajax使用小问题
wordpress_id: 351
wordpress_url: http://www.hijava.org/?p=351
date: 2009-05-04 14:18:25.000000000 +08:00
---
研究了两天的ExtJs，在制作树形菜单的时候卡住了，发现无论如何都无法从Json文件动态加载子菜单。仔细查阅了下教程才知道，导致这个问题的原因是没有将项目部署到WEB服务器上，一直都是用浏览器从本地打开预览。
<blockquote>一旦涉及到ajax就需要配合服务器了，ajax是无法从本地文件系统直接取得数据的。</blockquote>
这个问题整整折腾了我一天，哎...
