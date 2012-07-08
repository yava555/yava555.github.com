---
layout: post
title: Java Properties中文乱码问题解决
wordpress_id: 319
wordpress_url: http://www.hijava.org/?p=319
date: 2009-04-13 21:25:29.000000000 +08:00
---
用Properties读取Java属性文件的时候，会出现中文乱码的情况，这时就需要用JDK Bin目录下小工具native2ascii.exe了，native2ascii 转换实用程序允许进行源码编码，生成以 ISO 8859-1 编码的输出。在命令提示符下执行：

native2ascii -encoding gb2312 source.properties object.properties

另外也可以用UltralEdit另存为Unicode-ASCII Escaped格式进行转换。
<h4><strong>为什么要进行转换呢？</strong></h4>
<blockquote>Properties的输入/输出流采用的 ISO 8859-1 字符编码的格式，所以就用到了Unicode转义，来处理此编码中无法直接表示的字符。</blockquote>
