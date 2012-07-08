---
layout: post
title: JVM 类加载替换问题
wordpress_id: 522
wordpress_url: http://www.hijava.org/?p=522
date: 2009-11-12 19:27:42.000000000 +08:00
---
今天同事的tomcat突然不支持热部署了，修改了类之后，查看eclipse的 class文件输出目录，编译的class文件是最新的。并且DevLoader配置也没有问题，就将问题确定在JVM加载的过程上。Google搜索的时候，发现一篇文章<a href="http://www.jug.mk/blogs/ipenov/entry/hotswapping_using_jvm" target="_blank">'HotSwapping' using JVM</a> 得知HotSwap只能用在JVM的bebug模式下，将tomcat启动方式改为debug之后，果然解决了这个问题。
Java Debug Interface:<a href="http://java.sun.com/javase/6/docs/jdk/api/jpda/jdi/index.html" target="_blank">http://java.sun.com/javase/6/docs/jdk/api/jpda/jdi/index.html</a>
