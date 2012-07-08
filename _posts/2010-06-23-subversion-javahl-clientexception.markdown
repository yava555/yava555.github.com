---
layout: post
title: subversion.javahl.ClientException
wordpress_id: 769
wordpress_url: http://www.hijava.org/?p=769
date: 2010-06-23 20:26:26.000000000 +08:00
---
今天用在Eclipse使用subclipse插件的时候，遇到一个问题:
<blockquote>org.tigris.subversion.javahl.ClientException: Couldn't perform atomic initialization svn: Couldn't perform atomic initialization
Authorization failed
svn: Could not initialize the SASL library</blockquote>
查了好长时间都没有找到解决方式，无意间在SVN配置中将SVN接口 Client由JavaHL(Jni) 改成 Svn Kit(Pure Java)，竟然好了。

<a href="/uploads/2010/06/subclipse.jpg"><img class="alignnone size-full wp-image-770" title="subclipse" src="/uploads/2010/06/subclipse.jpg" alt="" width="438" height="349" /></a>

后来查了下，JavaHL和Svn Kit都是Subclipse SVN客户端与SVN服务交互的一种方式，JavaHL使用JNI的调用SVN的本地库，速度快，稳定可靠。

同事说的对，不能太依靠于搜索引擎去查找相同的问题的解决方式，遇到问题先自己静下心来分析一下，远比漫无目的的搜索强得多。
