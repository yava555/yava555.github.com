---
layout: post
title: WebView宽度自适应
wordpress_id: 1082
wordpress_url: http://www.hijava.org/?p=1082
date: 2011-06-18 20:56:07.000000000 +08:00
---
用WebView组件显示普通网页时一般会出现横向滚动条，这样会导致页面查看起来非常不方便。其实通过设置WebSettings的属性可以轻易地解决此问题，不过此设置隐藏的比较深，一般很少人会用到。
	webSettings= webView.getSettings();
	webSettings.setLayoutAlgorithm(LayoutAlgorithm.SINGLE_COLUMN);
LayoutAlgorithm是一个枚举，用来控制html的布局，总共有三种类型：
NORMAL：正常显示，没有渲染变化。
SINGLE_COLUMN：把所有内容放到WebView组件等宽的一列中。
NARROW_COLUMNS：可能的话，使所有列的宽度不超过屏幕宽度。
