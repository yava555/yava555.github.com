---
layout: post
title: Eclipse不能自动编译
wordpress_id: 484
wordpress_url: http://www.hijava.org/?p=484
date: 2009-09-15 11:11:23.000000000 +08:00
---
将Eclipse的Build Path中引入的所有Libraries全部删除，然后重新引入，就解决了。原因可能是引入了实际路径中不存在的Jar包。

还有其它导致Eclipse不能自动编译的原因，参照：<a href="http://www.blogjava.net/javafield/archive/2008/01/05/172940.html">http://www.blogjava.net/javafield/archive/2008/01/05/172940.html</a>
