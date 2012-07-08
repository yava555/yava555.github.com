---
layout: post
title: 豆瓣最新电影排行
wordpress_id: 831
wordpress_url: http://www.hijava.org/?p=831
date: 2010-08-03 23:44:23.000000000 +08:00
---
最近老想看电影，把豆瓣和迅雷翻了个底朝天也没找到几个合适的，主要是这些网站都不提供按照评分排序的功能。于是利用周末的时间，写了个爬虫，先爬取豆瓣上的电影，然后再按照用户评分从高到低排序输出。最后会生成一个网页，如下图所示：

<a href="/uploads/2010/08/movie.jpg"></a><a href="/uploads/2010/08/movie.jpg"></a><a href="/uploads/2010/08/movie1.jpg"><img class="alignnone size-full wp-image-835" title="douban movie" src="/uploads/2010/08/movie1.jpg" alt="" width="610" height="362" /></a>

底层用到了之前介绍的<a href="http://www.hijava.org/code/httpbot-web-crawler" target="_blank">HttpBot</a>，生成结果网页用到了<a href="http://velocity.apache.org/" target="_blank">volecity</a>，获取电影信息（评分、评价数、上映时间...）用的是正则表达式，其它就没什么特别的了。

程序还有很多不足，日后慢慢完善了...
