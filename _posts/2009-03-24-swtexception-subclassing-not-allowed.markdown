---
layout: post
title: ! 'SWTException: Subclassing not allowed'
wordpress_id: 274
wordpress_url: http://www.hijava.org/?p=274
date: 2009-03-24 10:36:40.000000000 +08:00
---
由于设计了一个类继承Shell，导致出现了“SWTException: Subclassing not allowed”错误。搜索了一下才知道， 				<span lang="EN-US">Shell</span> <span style="font-family: 宋体;">是可以被继承的，但</span> <span lang="EN-US">Shell</span> <span style="font-family: 宋体;">的父类</span> <span lang="EN-US">Decorations</span> <span style="font-family: 宋体;">有一个</span> <span lang="EN-US">checkSubclass ()</span> <span style="font-family: 宋体;">函数，当其子类不符合此方法的检查规则时，就会抛出异常。因此不是简单继承</span> <span lang="EN-US">Shell</span> <span style="font-family: 宋体;">就行了的，还要做一些比较复杂的工作。</span>

因此我们有三种方式可以解决这类异常：
<ol>
	<li><span style="font-family: 宋体;">聚合优于继承，采用聚合方式解决，也符合面向对象的设计原则</span></li>
	<li>重写				<span lang="EN-US">checkSubclass ()</span>方法，去掉基类的验证检查</li>
	<li>加上“package org.eclipse.swt.widgets”，让被扩展的类与扩展类处于同一类层次</li>
</ol>
