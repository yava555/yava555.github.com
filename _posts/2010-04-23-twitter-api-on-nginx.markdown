---
layout: post
title: 利用nginx搭建twitter api
wordpress_id: 685
wordpress_url: http://www.hijava.org/?p=685
date: 2010-04-23 16:10:22.000000000 +08:00
---
不知怎么搞得，之前一直用的twitter api突然失效了，无奈只好自己搭建api了。幸好利用nginx的反向代理就可以实现这个功能，配置很简单，只要修改一下nginx的配置文件（nginx.conf）就可以了：
	server {
		listen 80;
		server_name t.hijava.org;
		location / {
		proxy_pass http://twitter.com/;
		proxy_redirect off;
		proxy_set_header X-Real-IP $remote_addr;
		proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
	}

转自：<a href="http://lazyhack.net/twitter-api-with-nginx/" target="_blank">http://lazyhack.net/twitter-api-with-nginx/</a>
