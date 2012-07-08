---
layout: post
title: Tomcat虚拟目录设置
wordpress_id: 154
wordpress_url: http://www.hijava.org/?p=154
date: 2009-01-11 21:32:37.000000000 +08:00
---
今天为了给你朋友通过校园网传送文件，因为不在同一个网段内，IPMessenger无法找到对方，只好在自己电脑上用tomcat做了一个Http服务器。但是总不能将所有文件拷贝到webapps\ROOT下吧，Google了一下，找到了tomcat设置虚拟目录的方式。

在server.xml中加入&lt;Context&gt;元素，在名为“localhost”的&lt;Host&gt;元素中加入如下&lt;Context&gt;元素：

&lt;Context path="/down" docBase="F:\data" reloadable="true" /&gt;

path：指定访问该web应用的URL入口，docBase：指定Web应用的实际文件路径，可以是绝对路径，也可以是相对于&lt;Host&gt;的appBase属性的相对路径。
