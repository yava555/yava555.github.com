---
layout: post
title: ! '[转]forward和redirect的区别'
wordpress_id: 286
wordpress_url: http://www.hijava.org/java/forward%e5%92%8credirect%e7%9a%84%e5%8c%ba%e5%88%ab
date: 2009-04-08 17:03:53.000000000 +08:00
---
在Servlet中两种实现：
forward方式：request.getRequestDispatcher("/somePage.jsp").forward(request, response);
redirect方式：response.sendRedirect("/somePage.jsp");
forward是服务器内部重定向，程序收到请求后重新定向到另一个程序，客户机并不知道；redirect则是服务器收到请求后发送一个状态头给客 户，客户将再请求一次，这里多了两次网络通信的来往。当然forward也有缺点，就是forward的页面的路径如果是相对路径就会有些问题了。
forward 会将 request state , bean 等等信息带往下一个 jsp
redirect 是送到 client 端后再一次 request , 所以资料不被保留.
使用 forward 你就可以用 getAttribute() 来取的前一个 jsp 所放入的 bean 等等资料

在网上看到一些帖子，总结了一些区别，可以从以下几个方面来看：

1.从地址栏显示来说

forward是服务器请求资源,服务器直接访问目标地址的URL,把那个URL的响应内容读取过来,然后把这些内容

再发给浏览器.浏览器根本不知道服务器发送的内容从哪里来的,所以它的地址栏还是原来的地址.

redirect是服务端根据逻辑,发送一个状态码,告诉浏览器重新去请求那个地址.所以地址栏显示的是新的URL.所

以redirect等于客户端向服务器端发出两次request，同时也接受两次response。

2.从数据共享来说

forward:转发页面和转发到的页面可以共享request里面的数据.
redirect:不能共享数据.

redirect不仅可以重定向到当前应用程序的其他资源,还可以重定向到同一个站点上的其他应用程序中的资源,

甚至是使用绝对URL重定向到其他站点的资源.

forward,方法只能在同一个Web应用程序内的资源之间转发请求.

forward 是服务器内部的一种操作.
redirect 是服务器通知客户端,让客户端重新发起请求.

所以,你可以说 redirect 是一种间接的请求, 但是你不能说"一个请求是属于forward还是redirect "

3.从运用地方来说

forward:一般用于用户登陆的时候,根据角色转发到相应的模块.

redirect:一般用于用户注销登陆时返回主页面和跳转到其它的网站等.

4.从效率来说
forward:高.
redirect:低.

5.jsp 语法

	<jsp:forward page={"relativeurl" | "<%= expression %>"} />

或者这样写：

	<jsp:forward page={"relativeurl" | "<%= expression %>"} >

	<jsp:param name="parametername" value="{parametervalue | <%= expression %>}" />+

	</jsp:forward>

6.例子

	<jsp:forward page="/servlet/login" />

	<jsp:forward page="/servlet/login">

	<jsp:param name="username" value="jsmith" />

	</jsp:forward>

描述

<jsp:forward>标签从一个jsp文件向另一个文件传递一个包含用户请求的request对象.<jsp:forward>标签以下的代码，将不能执行.

你能够向目标文件传送参数和值，在这个例子中我们传递的参数名为username,值为scott,如果你使用了<jsp:param>标签的话，目标文件必须是一个动态的文件，能够处理参数.

如果你使用了非缓冲输出的话，那么使用<jsp:forward>时就要小心。
如果在你使用<jsp:forward>之前，jsp文件已经有了数据，那么文件执行就会出错.

属性

page="{relativeurl | <%= expression %>}"
这里是一个表达式或是一个字符串用于说明你将要定向的文件或url.这个文件可以是jsp,程序段，或者其它能够处理request对象的文件(如asp,cgi,php).

<jsp:param name="parametername" value="{parametervalue | <%= expression %>}" />+
向一个动态文件发送一个或多个参数，这个文件一定是动态文件.

如果你想传递多个参数，你可以在一个jsp文件中使用多个<jsp:param>。name指定参数名，value指定参数值.

<jsp:forward>例子

	<%@ page contentType="text/html;charset=gb2312" %>

	<html>

	       <head>
		      <title>test</title>
	       </head>

	       <body>

		      <jsp:forward page="forwardTo.jsp">
		             <jsp:param name="userName" value="riso"/>
		      </jsp:forward>

	       </body>

	</html>


forwardTo.jsp

	<%@ page contentType="text/html;charset=gb2312" %>

	<!--forwardTo.jsp-->

	<%

	String useName=request.getParameter("userName");

	String outStr= "谢谢光临！";

	outStr+=useName;

	out.println(outStr);

	%>

redirect的例子：

譬如：client 通过XXX\index.jsp?name=gauss&pwd=123访问index.jsp,而index.jsp中有< jsp:forward page="login.jsp"/>,则在login.jsp中可以通过request.getParameter()得到name和pwd， 而<%response.sendRedirect("login.jsp");%>得不到。
