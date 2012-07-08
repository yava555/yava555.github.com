---
layout: post
title: jsp include乱码
wordpress_id: 430
wordpress_url: http://www.hijava.org/?p=430
date: 2009-06-03 07:20:55.000000000 +08:00
---
采用&lt;jsp:include page=""&gt;&lt;/jsp:include&gt;包含页面时，被包含页面的动态内容部分出现乱码，无论怎么设置被包含页面的pageEncoding和contentType都不管用，浪费了很长时间解决这个问题。后来发现，在包含与被包含页面都加上：&lt;%@ page import="java.util.*" contentType="text/html;UTF-8" pageEncoding="UTF-8" %&gt;就可以解决了。
