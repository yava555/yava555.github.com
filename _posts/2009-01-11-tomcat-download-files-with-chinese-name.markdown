---
layout: post
title: Tomcat带中文名的文件下载
wordpress_id: 157
wordpress_url: http://www.hijava.org/?p=157
date: 2009-01-11 21:48:31.000000000 +08:00
---
今天用Tomcat作为服务器提供文件下载的时候，发现无法找到名称带中文的文件。

在\conf\server.xml文件中的&lt;Connector&gt;元素中加入URIEncoding="UTF-8"，即可以解决这个问题，加入后的代码如下：

&lt;Connector port="8080" protocol="HTTP/1.1" connectionTimeout="20000" redirectPort="8443" URIEncoding="UTF-8" /&gt;
