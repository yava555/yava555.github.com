---
layout: post
title: HttpURLConnection cookie管理
wordpress_id: 111
wordpress_url: http://www.hijava.org/?p=111
date: 2008-11-17 17:00:33.000000000 +08:00
---
但我们使用HttpURLConnection访问web页面的时候不免要涉及到cookie处理，下面简要的介绍一下如何获取和发送相关的cookie
	String cookieVal = null;
	String key=null;
	   for (int i = 1; (key = http.getHeaderFieldKey(i)) != null; i++ ) {
	      if (key.equalsIgnoreCase("set-cookie")) {
	    	  cookieVal = http.getHeaderField(i);
	    	  cookieVal = cookieVal.substring(0, cookieVal.indexOf(";"));
	    	  sessionId=sessionId+cookieVal+";";
	      }
	   }
其中sessionId就是获取到的cookie，当我们访问需要授权的页面时，将cookie写入到http请求的头部就可以了。如下所示：
	http.setRequestProperty("Cookie", sessionId);
