---
layout: post
title: 什么是Web Service
wordpress_id: 736
wordpress_url: http://www.hijava.org/?p=736
date: 2010-05-20 23:03:53.000000000 +08:00
---
<h3>一、Web Service定义</h3>
<blockquote>A Web service is a software system identified by a URI , whose  public interfaces and bindings are defined and described using XML. Its definition can be discovered by other software systems. These systems may then interact with the Web service in a manner prescribed by its definition, using XML based messages conveyed by Internet protocols.</blockquote>
这是W3C工作组对Web Service下的定义。通常Web Service包括三个基本元素：<a title="WSDL" href="http://www.w3.org/TR/wsdl" target="_blank">WSDL</a>（Web Services Description Language）、<a title="SOAP" href="http://www.w3.org/TR/soap/" target="_blank">SOAP</a>（Simple Object Access Protocol）和<a title="UDDI" href="http://www.uddi.org/" target="_blank">UDDI</a>（Universal Description, Discovery, and Integration），通过Web Service的定义中也能大致看出来。
<ol>
	<li>WSDL：一个XML格式文档，用以描述服务端口访问方式和使用协议的细节。通常用来辅助生成服务器和客户端代码及配置信息。</li>
	<li>SOAP：一个基于XML的可扩展消息信封格式，需同时绑定一个传输用协议。这个协议通常是HTTP或HTTPS，但也可能是SMTP或XMPP。</li>
	<li>UDDI：一个用来发布和搜索WEB服务的协议，应用程序可借由此协议在设计或运行时找到目标WEB服务。</li>
</ol>
使用Web Service的三种最普遍的方式：<a title="远程过程调用" href="http://zh.wikipedia.org/wiki/%E8%BF%9C%E7%A8%8B%E8%BF%87%E7%A8%8B%E8%B0%83%E7%94%A8" target="_blank">远程过程调用</a>（RPC）、<a title="面向服务架构" href="http://zh.wikipedia.org/wiki/%E9%9D%A2%E5%90%91%E6%9C%8D%E5%8A%A1%E6%9E%B6%E6%9E%84" target="_blank">面向服务架构</a>（SOA）以及表述性状态转移（<a title="REST" href="http://zh.wikipedia.org/wiki/REST" target="_blank">REST</a>）。

JavaEye上有两篇关于Web Service的讨论贴：<a href="http://www.javaeye.com/topic/662787" target="_blank">SOAP和WebService的那些事</a> 和 <a href="http://www.javaeye.com/topic/410195" target="_blank">关于 Web Service 的一些理解</a> ，可以加深对Web Service的了解。
<h3>二、Web Service架构</h3>
<p style="text-align: center;"><a href="/uploads/2010/05/web_service_architecture.jpg"><img class="size-full wp-image-744  aligncenter" title="web_service_architecture" src="/uploads/2010/05/web_service_architecture.jpg" alt="" width="500" height="363" /></a></p>
<p style="text-align: center;">Web Services Architecture</p>
<p style="text-align: center;"><a href="/uploads/2010/05/web_service_stack.jpg"><img class="size-full wp-image-745   aligncenter" title="web_service_stack" src="/uploads/2010/05/web_service_stack.jpg" alt="" width="500" height="331" /></a>Web Services Stack</p>

<h3>三、参考：</h3>
<a href="http://zh.wikipedia.org/zh-cn/Web_service" target="_blank">http://zh.wikipedia.org/zh-cn/Web_service</a>

<a href="http://www.genomeutwin.org/events/SENGER_060504_webservices.ppt" target="_blank">http://www.genomeutwin.org/events/SENGER_060504_webservices.ppt</a>

<a href="http://www.michaelweiss.ca/courses/comp/5401/lectures/07-Web-Services.pdf" target="_blank">http://www.michaelweiss.ca/courses/comp/5401/lectures/07-Web-Services.pdf</a>
