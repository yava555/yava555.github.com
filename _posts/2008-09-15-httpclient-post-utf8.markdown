---
layout: post
title: ! '[转]HttpClient POST 的 UTF-8 编码问题'
wordpress_id: 64
wordpress_url: http://www.hijava.org/?p=64
date: 2008-09-15 21:42:11.000000000 +08:00
---
<h3>问题分析</h3>
不过在实际使用中, 还是发现按照最基本的方式调用 HttpClient 时, 并不支持 UTF-8 编码, 在网络上找过一些文章, 也不得要领, 于是查看了 commons-httpclient-3.0.1 的一些代码, 首先在 PostMethod 中找到了 generateRequestEntity() 方法:
<table style="table-layout: fixed;" border="2" cellspacing="0" cellpadding="3" align="center" bgcolor="#ffffff">
<tbody>
<tr>
<td style="font-size: smaller;" align="left" valign="top"><code style="font-family: 'Courier New'; font-size: 9pt;"><span style="color: #ffffff;"> </span><span style="color: #008000;">/**</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">* Generates a request entity from the post parameters, if present.  Calls</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">* </span><span style="color: #008000;">{@link EntityEnclosingMethod#generateRequestBody()} </span><span style="color: #008000;">if parameters have not been set.</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">* </span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">* </span><span style="color: #005500;">@since </span><span style="color: #008000;">3.0</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">*/</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>protected </strong></span><span style="color: #000000;">RequestEntity generateRequestEntity</span><span style="color: #000000;">() {</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>if </strong></span><span style="color: #000000;">(</span><span style="color: #000000;">!</span><span style="color: #0000c0;"><strong>this</strong></span><span style="color: #000000;">.params.isEmpty</span><span style="color: #000000;">()) {</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">// Use a ByteArrayRequestEntity instead of a StringRequestEntity.</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">// This is to avoid potential encoding issues.  Form url encoded strings</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">// are ASCII by definition but the content type may not be.  Treating the content</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">// as bytes allows us to keep the current charset without worrying about how</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">// this charset will effect the encoding of the form url encoded string.</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">String content = EncodingUtil.formUrlEncode</span><span style="color: #000000;">(</span><span style="color: #000000;">getParameters</span><span style="color: #000000;">()</span><span style="color: #000000;">, getRequestCharSet</span><span style="color: #000000;">())</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">ByteArrayRequestEntity entity = </span><span style="color: #0000c0;"><strong>new </strong></span><span style="color: #000000;">ByteArrayRequestEntity</span><span style="color: #000000;">(</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">EncodingUtil.getAsciiBytes</span><span style="color: #000000;">(</span><span style="color: #000000;">content</span><span style="color: #000000;">)</span><span style="color: #000000;">,</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">FORM_URL_ENCODED_CONTENT_TYPE</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">)</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>return </strong></span><span style="color: #000000;">entity;</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">} </span><span style="color: #0000c0;"><strong>else </strong></span><span style="color: #000000;">{</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>return super</strong></span><span style="color: #000000;">.generateRequestEntity</span><span style="color: #000000;">()</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">}</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">}</span></code></td>
</tr>
</tbody></table>
原来使用 NameValuePair 加入的 HTTP 请求的参数最终都会转化为 RequestEntity 提交到 HTTP 服务器, 接着在 PostMethod 的父类 EntityEnclosingMethod 中找到了如下的代码:
<table style="table-layout: fixed;" border="2" cellspacing="0" cellpadding="3" align="center" bgcolor="#ffffff">
<tbody>
<tr>
<td style="font-size: smaller;" align="left" valign="top"><code style="font-family: 'Courier New'; font-size: 9pt;"><span style="color: #ffffff;"> </span><span style="color: #008000;">/**</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">* Returns the request's charset.  The charset is parsed from the request entity's </span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">* content type, unless the content type header has been set manually. </span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">* </span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">* </span><span style="color: #005500;">@see </span><span style="color: #008000;">RequestEntity#getContentType()</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">* </span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">* </span><span style="color: #005500;">@since </span><span style="color: #008000;">3.0</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">*/</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>public </strong></span><span style="color: #000000;">String getRequestCharSet</span><span style="color: #000000;">() {</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>if </strong></span><span style="color: #000000;">(</span><span style="color: #000000;">getRequestHeader</span><span style="color: #000000;">(</span><span style="color: #990000;">"Content-Type"</span><span style="color: #000000;">) </span><span style="color: #000000;">== </span><span style="color: #0000c0;"><strong>null</strong></span><span style="color: #000000;">) {</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">// check the content type from request entity</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">// We can't call getRequestEntity() since it will probably call</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">// this method.</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>if </strong></span><span style="color: #000000;">(</span><span style="color: #0000c0;"><strong>this</strong></span><span style="color: #000000;">.requestEntity != </span><span style="color: #0000c0;"><strong>null</strong></span><span style="color: #000000;">) {</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>return </strong></span><span style="color: #000000;">getContentCharSet</span><span style="color: #000000;">(</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>new </strong></span><span style="color: #000000;">Header</span><span style="color: #000000;">(</span><span style="color: #990000;">"Content-Type"</span><span style="color: #000000;">, requestEntity.getContentType</span><span style="color: #000000;">()))</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">} </span><span style="color: #0000c0;"><strong>else </strong></span><span style="color: #000000;">{</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>return super</strong></span><span style="color: #000000;">.getRequestCharSet</span><span style="color: #000000;">()</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">}</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">} </span><span style="color: #0000c0;"><strong>else </strong></span><span style="color: #000000;">{</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>return super</strong></span><span style="color: #000000;">.getRequestCharSet</span><span style="color: #000000;">()</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">}</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">}</span></code></td>
</tr>
</tbody></table>
<h3>解决方案</h3>
从上面两段代码可以看出是 HttpClient 是如何依据 "Content-Type" 获得请求的编码(字符集), 而这个编码又是如何应用到提交内容的编码过程中去的. 按照这个原来, 其实我们只需要重载 getRequestCharSet() 方法, 返回我们需要的编码(字符集)名称, 就可以解决 UTF-8 或者其它非默认编码提交 POST 请求时的乱码问题了.
<h3>测试</h3>
首先在 Tomcat 的 ROOT WebApp 下部署一个页面 test.jsp, 作为测试页面, 主要代码片段如下:
<table style="table-layout: fixed;" border="2" cellspacing="0" cellpadding="3" align="center" bgcolor="#ffffff">
<tbody>
<tr>
<td style="font-size: smaller;" align="left" valign="top"><code style="font-family: 'Courier New'; font-size: 9pt;"><span style="color: #000000;">&lt;%@ page contentType=</span><span style="color: #990000;">"text/html;charset=UTF-8"</span><span style="color: #000000;">%&gt;</span>
<span style="color: #000000;">&lt;%@ page session=</span><span style="color: #990000;">"false" </span><span style="color: #000000;">%&gt;</span>
<span style="color: #000000;">&lt;%</span>
<span style="color: #000000;">request.setCharacterEncoding</span><span style="color: #000000;">(</span><span style="color: #990000;">"UTF-8"</span><span style="color: #000000;">)</span><span style="color: #000000;">;</span>
<span style="color: #000000;">String val = request.getParameter</span><span style="color: #000000;">(</span><span style="color: #990000;">"TEXT"</span><span style="color: #000000;">)</span><span style="color: #000000;">;</span>
<span style="color: #000000;">System.out.println</span><span style="color: #000000;">(</span><span style="color: #990000;">"&gt;&gt;&gt;&gt; The result is " </span><span style="color: #000000;">+ val</span><span style="color: #000000;">)</span><span style="color: #000000;">;</span>
<span style="color: #000000;">%&gt;</span></code></td>
</tr>
</tbody></table>
接着写一个测试类, 主要代码如下:
<table style="table-layout: fixed;" border="2" cellspacing="0" cellpadding="3" align="center" bgcolor="#ffffff">
<tbody>
<tr>
<td style="font-size: smaller;" align="left" valign="top"><code style="font-family: 'Courier New'; font-size: 9pt;"><span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>public static </strong></span><span style="color: #c00000;"><strong>void </strong></span><span style="color: #000000;">main</span><span style="color: #000000;">(</span><span style="color: #000000;">String</span><span style="color: #000000;">[] </span><span style="color: #000000;">args</span><span style="color: #000000;">) </span><span style="color: #0000c0;"><strong>throws </strong></span><span style="color: #000000;">Exception, IOException </span><span style="color: #000000;">{</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">String url = </span><span style="color: #990000;">"http://localhost:8080/test.jsp"</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">PostMethod postMethod = </span><span style="color: #0000c0;"><strong>new </strong></span><span style="color: #000000;">UTF8PostMethod</span><span style="color: #000000;">(</span><span style="color: #000000;">url</span><span style="color: #000000;">)</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">//填入各个表单域的值</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">NameValuePair</span><span style="color: #000000;">[] </span><span style="color: #000000;">data = </span><span style="color: #000000;">{</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>new </strong></span><span style="color: #000000;">NameValuePair</span><span style="color: #000000;">(</span><span style="color: #990000;">"TEXT"</span><span style="color: #000000;">, </span><span style="color: #990000;">"中文"</span><span style="color: #000000;">)</span><span style="color: #000000;">,</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">}</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">//将表单的值放入postMethod中</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">postMethod.setRequestBody</span><span style="color: #000000;">(</span><span style="color: #000000;">data</span><span style="color: #000000;">)</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">//执行postMethod</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">HttpClient httpClient = </span><span style="color: #0000c0;"><strong>new </strong></span><span style="color: #000000;">HttpClient</span><span style="color: #000000;">()</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">httpClient.executeMethod</span><span style="color: #000000;">(</span><span style="color: #000000;">postMethod</span><span style="color: #000000;">)</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">}</span>
<span style="color: #ffffff;"> </span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">//Inner class for UTF-8 support</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>public static class </strong></span><span style="color: #000000;">UTF8PostMethod </span><span style="color: #0000c0;"><strong>extends </strong></span><span style="color: #000000;">PostMethod</span><span style="color: #000000;">{</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>public </strong></span><span style="color: #000000;">UTF8PostMethod</span><span style="color: #000000;">(</span><span style="color: #000000;">String url</span><span style="color: #000000;">){</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>super</strong></span><span style="color: #000000;">(</span><span style="color: #000000;">url</span><span style="color: #000000;">)</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">}</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">@Override</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>public </strong></span><span style="color: #000000;">String getRequestCharSet</span><span style="color: #000000;">() {</span>
<span style="color: #ffffff;"> </span><span style="color: #008000;">//return super.getRequestCharSet();</span>
<span style="color: #ffffff;"> </span><span style="color: #0000c0;"><strong>return </strong></span><span style="color: #990000;">"UTF-8"</span><span style="color: #000000;">;</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">}</span>
<span style="color: #ffffff;"> </span><span style="color: #000000;">}</span></code></td>
</tr>
</tbody></table>
运行这个测试程序, 在 Tomcat 的后台输出中可以正确打印出 "&gt;&gt;&gt;&gt; The result is 中文" .

转自：http://thinkbase.net/w/main/Wiki?action=action_search&amp;text=%22HttpClient+POST+%E7%9A%84+UTF-8+%E7%BC%96%E7%A0%81%E9%97%AE%E9%A2%98%22<br class="Apple-interchange-newline" />
