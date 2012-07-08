---
layout: post
title: 如何在Linux上安装Squid代理服务器软件
wordpress_id: 639
wordpress_url: http://www.hijava.org/?p=639
date: 2010-04-04 23:06:17.000000000 +08:00
---
<h3>1、获取Squid源代码</h3>
	wget ftp://ftp.cuhk.edu.hk/pub/packages/info-systems/www/squid/squid-3.1.1.tar.gz
<h3>2、编译及安装</h3>
	tar -zxvf squid-3.1.1.tar.gz
	cd squid-3.1.1
	./configure --prefix=/usr/local/squid --enable-arp-acl --enable-linux-netfilter --enable-pthreads --enable-err-language="Simplify_Chinese" --enable-default-err-language="Simplify_Chinese" --enable-auth="basic" --enable-baisc-auth-helpers="NCSA" --enable-underscore
	make
	make install
<h3>3、编译生成Squid认证程序ncsa_auth</h3>
	cd helpers/basic_auth/NCSA/
	make
	cp ncsa_auth /usr/sbin/
	cd ../../../
<h3>4、使用htpasswd来生成用户名/密码对应的文件</h3>
	htpasswd -c /usr/local/squid/password hijava
在输入两边密码后，一个hijava用户就生成了。如果以后需要添加用户，把上面的命令去掉-c参数再运行即可。
<h3>5、修改Squid配置文件</h3>
	cd /usr/local/squid/
	mv -f etc/squid.conf etc/squid.conf.bak
	vi etc/squid.conf
插入如下内容：
	acl SSL_ports port 443
	acl Safe_ports port 80		# http
	acl Safe_ports port 21		# ftp
	acl Safe_ports port 443		# https
	acl Safe_ports port 70		# gopher
	acl Safe_ports port 210		# wais
	acl Safe_ports port 1025-65535	# unregistered ports
	acl Safe_ports port 280		# http-mgmt
	acl Safe_ports port 488		# gss-http
	acl Safe_ports port 591		# filemaker
	acl Safe_ports port 777		# multiling http
	acl CONNECT method CONNECT

	auth_param basic program /usr/sbin/ncsa_auth /usr/local/squid/password
	acl normal proxy_auth REQUIRED
	http_access allow normal

	# Deny requests to certain unsafe ports
	http_access deny !Safe_ports

	# Deny CONNECT to other than secure SSL ports
	http_access deny CONNECT !SSL_ports

	# And finally deny all other access to this proxy
	http_access deny all

	# Squid normally listens to port 3128
	http_port 3128

	# We recommend you to use at least the following line.
	hierarchy_stoplist cgi-bin ?

	# Uncomment and adjust the following to add a disk cache directory.
	#cache_dir null /tmp

	# Leave coredumps in the first cache dir
	coredump_dir /usr/local/squid/var/cache

	# Add any of your own refresh_pattern entries above these.
	refresh_pattern ^ftp:		1440	20%	10080
	refresh_pattern ^gopher:	1440	0%	1440
	refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
	refresh_pattern .		0	20%	4320
<h3>6、启动Squid</h3>
	 ./sbin/squid

参考：<a href="http://wiki.ubuntu.org.cn/Squid%E9%85%8D%E7%BD%AE%E8%AF%A6%E8%A7%A3" target="_blank">http://wiki.ubuntu.org.cn/Squid%E9%85%8D%E7%BD%AE%E8%AF%A6%E8%A7%A3</a>
