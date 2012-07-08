---
layout: post
title: Eclipse 3.5 Ant运行中断问题
wordpress_id: 493
wordpress_url: http://www.hijava.org/?p=493
date: 2009-09-25 22:29:20.000000000 +08:00
---
在Eclipse3.5里运行Ant的时候会莫名其妙地中断，导致无法成功构建项目。可能是由于Eclipse中Ant默认的Logger导致的。解决办法：运行Ant，弹出Edit Configration窗口，选择Main选项卡，在Arguments处添加参数“-logger org.apache.tools.ant.NoBannerLogger”。

详细内容：<a href="http://hi.baidu.com/zh_m_zhou/blog/item/2772d0171f442e58f2de3257.html" target="_blank">http://hi.baidu.com/zh_m_zhou/blog/item/2772d0171f442e58f2de3257.html</a>
