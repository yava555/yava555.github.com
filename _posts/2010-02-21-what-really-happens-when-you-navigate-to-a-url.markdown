---
layout: post
title: 当你输入一个网址之后，实际上发生了些什么？
wordpress_id: 542
wordpress_url: http://www.hijava.org/?p=542
date: 2010-02-21 20:28:51.000000000 +08:00
---
今天读了一篇不错的文章<a href="http://igoro.com/archive/what-really-happens-when-you-navigate-to-a-url/" target="_blank">What really happens when you navigate to a URL</a> ，作者用示例形象地描述了浏览器与服务器的整个交互过程。
<ol>
	<li>在浏览器里输入网址</li>
	<li>浏览器查找服务器的IP地址（浏览器缓存 -&gt; 操作系统缓存 -&gt; 路由器缓存 -&gt; DNS服务器 ）</li>
	<li>浏览器向WEB服务器发出HTTP请求</li>
	<li>服务器处理请求（ASP,JSP,PHP...解析器解析）</li>
	<li>服务器返回响应的HTML代码</li>
	<li>浏览器开始解析渲染HTML</li>
	<li>于此同时，浏览器对于碰到的嵌入在HTML里的对象发起HTTP请求（Images,CSS,JS）</li>
</ol>
这只是一个大体流程，每一个环节都可以延伸出很多技术来，像<a href="http://baike.baidu.com/view/21895.htm" target="_blank">CDN</a>,<a href="http://www.ietf.org/rfc/rfc2616.txt" target="_blank">Http Protocol</a>,<a href="http://baike.baidu.com/view/22276.htm" target="_blank">DNS</a>… 需要每一个WEB开发人员去深入钻研。

中文翻译：<a href="http://article.yeeyan.org/view/54517/91367" target="_blank">http://article.yeeyan.org/view/54517/91367</a>
