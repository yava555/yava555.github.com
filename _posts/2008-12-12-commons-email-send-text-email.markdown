---
layout: post
title: 利用Commons Email发送文本邮件
wordpress_id: 140
wordpress_url: http://www.hijava.org/?p=140
date: 2008-12-12 22:13:35.000000000 +08:00
---
<blockquote>Commons Email aims to provide a API for sending email. It is built on top of the Java Mail API, which it aims to simplify.</blockquote>
	SimpleEmail email=new SimpleEmail();
	email.setHostName("smtp.163.com");//设置smpt服务器
	email.setFrom("yava555@163.com", "yava");
	email.setAuthentication("yava555@163.com", "******");//用户名和密码

	email.addTo("yava555@gmail.com","yava");//要发送邮箱

	email.setSubject("测试");
	email.setCharset("gb2312");//设置编码，必须在setMsg()之前
	email.setMsg("哈哈，测试一下:)");
	email.send();
Commons-Email构建在JavaMail基础之上，因此必须将JavaMail-API加入到环境变量中。
Commons Email:<a href="http://commons.apache.org/email/" target="_self">http://commons.apache.org/email/</a>
