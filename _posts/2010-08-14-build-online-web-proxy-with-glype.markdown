---
layout: post
title: 利用Glype搭建在线网页代理
wordpress_id: 840
wordpress_url: http://www.hijava.org/?p=840
date: 2010-08-14 20:59:35.000000000 +08:00
---
<a href="http://www.glype.com/" target="_blank">Glype proxy script</a> 是一个强大的开源网页代理程序，使用它可以非常方便的搭建一个在线代理网站。

目前最新版本为glype-1.1，要求服务器支持PHP5(及以上)，并且能够开启cURL。

<a href="../wp-content/uploads/2010/08/glype.jpg"><img title="glype" src="../wp-content/uploads/2010/08/glype.jpg" alt="" width="400" height="300" /></a>

安装完后访问GFW黑名单里的站点，仍然会被重置，经过base64编码过的URL也能被检测出来，GFW越来越强大了。

这时就需要修改一下settings.php文件中<em> $CONFIG['unique_urls']=false</em>，将false改成true，就不会出现网页被重置的问题了。
