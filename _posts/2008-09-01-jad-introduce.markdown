---
layout: post
title: Jad Java反编译工具
wordpress_id: 31
wordpress_url: http://www.hijava.org/?p=31
date: 2008-09-01 22:38:42.000000000 +08:00
---
Jad是一个简单易用的反编译工具，可以将二进制字节码文件转换成源文件。今天用jad反编译了下写过的一个class文件，结果让我大吃一惊，反编译出来的代码和源文件差别很小。

一、基本用法
Usage:<span class="hilite1">jad</span> [option(s)]
直接输入类文件名，且支持通配符，如下所示。
c:\Java\&gt;<span class="hilite1">jad</span> example1.class
c:\Java\&gt;<span class="hilite1">jad</span> *.class
结果是将example1.class反编译为example1.<span class="hilite1">jad</span>。将example1.<span class="hilite1">jad</span>改为example1.Java即得源文件。

二、Option -o
不提示，覆盖源文件

三、Option -s
c:\Java\&gt;<span class="hilite1">jad</span> -sJava example1.class
反编译结果以.Java为扩展名。

四、Option -p
将反编译结果输出到屏幕
c:\Java\&gt;<span class="hilite1">jad</span> -p example1.class
将反编译结果重定向到文件
c:\Java\&gt;<span class="hilite1">jad</span> -p example1.class&gt;example1.Java

五、Option -d
指定反编译的输出文件目录
c:\Java\&gt;<span class="hilite1">jad</span> -o -dtest -sJava *.class

官方网站：<a href="http://kpdus.com/jad.html">http://kpdus.com/jad.html</a>
