---
layout: post
title: SVN忽略thumbs.db
wordpress_id: 809
wordpress_url: http://www.hijava.org/?p=809
date: 2010-07-25 12:49:21.000000000 +08:00
---
烦人的thumbs.db文件，经常会给SVN提交带来不便，今天查了下，其实可以在SVN客户端做些设置，将其忽略掉。

<strong>如果使用的是Eclipse Subclipse插件</strong>

windows -&gt; performances -&gt; team -&gt; Ignored Resources -&gt; 添加*.db

<strong>如果使用的是TortoiseSVN客户端</strong>

右击鼠标-&gt; 选择 TortoiseSVN -&gt; Setting (设置) -&gt; General (常规设置) -&gt;  在右侧 "Golbal ignore pattern"(全局忽略样式)内填入*.db -&gt; 确定;
