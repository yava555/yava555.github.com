---
layout: post
title: 如何利用Nginx架设Http代理服务器
wordpress_id: 651
wordpress_url: http://www.hijava.org/?p=651
date: 2010-04-06 23:35:59.000000000 +08:00
---
<a href="http://zh.wikipedia.org/zh-cn/Nginx" target="_blank">Nginx</a>一般都是作为web服务器和反向代理服务器存在的，我们也可以把它用作一个Http代理服务器。操作很简单，只需要修改一下它的配置文件nginx.conf 添加一个Server字段。
	server {
	    listen 8080;
	    location / {
	    proxy_pass http://$http_host$request_uri;
	    access_log off;
	    }
	}
另外还需要在http字段内，用resolver指定一下DNS服务器，否则会发生 “nginx 502 bad gateway” 的错误。我采用是Google提供的DNS服务：
	resolver 8.8.8.8;
修改完之后需要重启一下nginx服务器：
	nginx -s reload

最后，修改一下浏览器代理设置的，访问<a href="http://www.ip.cn" target="_blank">www.ip.cn</a>，就能看到IP地址发生变化了。
<a href="/uploads/2010/04/ip.jpg"><img class="alignnone size-full wp-image-656" title="ip" src="/uploads/2010/04/ip.jpg" alt="" width="252" height="27" /></a>
