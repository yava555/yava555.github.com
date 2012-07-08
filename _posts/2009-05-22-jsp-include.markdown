---
layout: post
title: jsp:include与include伪指令的区别
wordpress_id: 413
wordpress_url: http://www.hijava.org/?p=413
date: 2009-05-22 20:49:25.000000000 +08:00
---
Jsp中两种包含页面的方式，静态包含与动态包含：

&lt;%@ include file="content.jsp"  %&gt;

&lt;jsp:include page="content.jsp"&gt;&lt;/jsp:include&gt;
<ol>
	<li>静态包含（include伪指令）：不会检查文件的变化，适合包含静态页面。在编译Servlet的时候，将两个页面融合到一个Servlet里。</li>
	<li>动态包含（jsp:include）：总是会检查文件中变化。生成两个Servlet文件，请求执行时，由Servlet相关对象去调用被包含页面对应的Servlet，JspRuntimeLibrary.include(request, response, "content.jsp", out, false);</li>
</ol>
