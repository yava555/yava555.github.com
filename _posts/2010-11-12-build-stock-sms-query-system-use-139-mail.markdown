---
layout: post
title: 利用139手机邮箱建立股票短信查询系统
wordpress_id: 956
wordpress_url: http://www.hijava.org/?p=956
date: 2010-11-12 18:00:10.000000000 +08:00
---
最近突然对股票很感兴趣，在学习的过程中就萌生了一个想法：“如果有一个股票短信查询系统该多好啊，发送股票代码到指定的号码，然后就能立马收到该股票实时信息”。经过一些技术调研之后，发现借助移动的139手机邮箱就可以实现该功能，一切都是免费的！
<h3>一、原理：</h3>
<ol>
	<li>移动139邮箱提供了“用短信发邮件的功能”，使用方式：发送短信 “邮件地址[空格或#]邮件主题[空格或#]邮件正文” 到10658139。
利用此功能，我们就可以用短信，将想要查询的股票代码发送到指定的邮箱 “getstock@126.com ”中。</li>
	<li>写程序，不断读取邮箱 “getstock@126.com ”中的邮件，得到股票代码和发件人邮箱地址。</li>
	<li>根据股票代码，利用<a href="http://www.morningstaredu.com/public_html/wordpress/%E6%96%B0%E6%B5%AA%E8%82%A1%E7%A5%A8%E6%9F%A5%E8%AF%A2%E6%8E%A5%E5%8F%A31.html" target="_blank">新浪股票查询接口</a>，获取实时股票数据。</li>
	<li>将股票数据，发送到第2步获得的发件人的邮箱中（移动会把139邮箱的邮件，自动以短信形式发送到用户手机上）。</li>
</ol>
<h3>二、使用方式：</h3>
<ol>
	<li>开通139邮箱，并且在邮箱的设置中开启“邮件到达通知”功能，手机接收方式最好选择长短信。</li>
	<li>发送短信 <strong>“getstock@126.com 600050” 到 10658139</strong> (后台服务已开启，欢迎大家测试)
注：600050是股票代码</li>
</ol>
<h3>三、延伸：</h3>
其实，利用此原理还可以做好多有趣的事情，例如发短信获取百科数据、发短信远程操作电脑... 主要看大家的想象力了。
<h3>四、源码下载：</h3>
<a href="/uploads/2010/11/StockSMS.zip">StockSMS.zip</a> 代码未整理，将就查看 :)
<h3>五、相关链接</h3>
<ol>
	<li> <a href="http://chinamobileshare.5d6d.com/thread-972-1-1.html" target="_blank">139手机邮箱短信操作指令汇总</a></li>
	<li> <a href="http://www.morningstaredu.com/public_html/wordpress/%E6%96%B0%E6%B5%AA%E8%82%A1%E7%A5%A8%E6%9F%A5%E8%AF%A2%E6%8E%A5%E5%8F%A31.html" target="_blank">新浪股票查询接口</a></li>
</ol>

原文地址：<a href="http://www.hijava.org/code/build-stock-sms-query-system-use-139-mail" target="_blank">http://www.hijava.org/code/build-stock-sms-query-system-use-139-mail</a>
