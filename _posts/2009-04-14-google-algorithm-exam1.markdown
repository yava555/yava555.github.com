---
layout: post
title: Google 笔试算法题
wordpress_id: 324
wordpress_url: http://www.hijava.org/?p=324
date: 2009-04-14 11:17:16.000000000 +08:00
---
<h4><strong>算法题目：</strong></h4>
有一台机器，上面有m个储存空间。然后有n个请求，第i个请求计算时需要占R[i]个空间，储存计算结果则需要占据O[i]个空间（其中 O[i]&lt;R[i]）。问怎么安排这n个请求的顺序，使得所有请求都能完成。你的算法也应该能够判断出无论如何都不能处理完的情况。
比方说，m=14，n=2，R[1]=10，O[1]=5，R[2]=8，O[2]=6。在这个例子中，我们可以先运行第一个任务，剩余9个单位的空间足够执行第二个任务；但如果先走第二个任务，第一个任务执行时空间就不够了，因为10&gt;14-6。
<h4><strong>解答：</strong></h4>
只需要按照R值和O值之差（即释放空间的大小）从大到小排序，依次处理请求就可以了。

转自：<a href="http://www.matrix67.com/blog/archives/1714" target="_blank">http://www.matrix67.com/blog/archives/1714</a>
