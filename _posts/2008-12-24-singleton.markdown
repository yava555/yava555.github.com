---
layout: post
title: ! '[转]设计模式之Singleton(单态) '
wordpress_id: 144
wordpress_url: http://www.hijava.org/?p=144
date: 2008-12-24 12:00:38.000000000 +08:00
---
<strong>单态定义</strong>:
Singleton模式主要作用是保证在Java应用程序中，一个类Class只有一个实例存在。

在很多操作中，比如建立目录 数据库连接都需要这样的单线程操作。

还有, singleton能够被状态化;  这样，多个单态类在一起就可以作为一个状态仓库一样向外提供服务，比如，你要论坛中的帖子计数器，每次浏览一次需要计数，单态类能否保持住这个计数，并且能synchronize的安全自动加1，如果你要把这个数字永久保存到数据库，你可以在不修改单态接口的情况下方便的做到。

另外方面，Singleton也能够被无状态化。提供工具性质的功能，

Singleton模式就为我们提供了这样实现的可能。使用Singleton的好处还在于可以节省内存，因为它限制了实例的个数，有利于Java垃圾回收（garbage  collection）。

我们常常看到工厂模式中类装入器(class  loader)中也用Singleton模式实现的,因为被装入的类实际也属于资源。

<strong>如何使用?</strong>
一般Singleton模式通常有几种形式:
	public class Singleton {

	private Singleton(){}

	//在自己内部定义自己一个实例，是不是很奇怪？
	//注意这是private 只供内部调用

	private static Singleton instance = new Singleton();

	//这里提供了一个供外部访问本class的静态方法，可以直接访问
	public static Singleton  getInstance() {
	return instance;
	}
	}
第二种形式:
	public class Singleton {

	private static Singleton instance = null;

	public static  synchronized Singleton getInstance() {
	if  (instance==null)
	instance＝new Singleton();
	return instance; 　　
	}

	}
使用Singleton.getInstance()可以访问单态类。

上面第二中形式是lazy initialization，也就是说第一次调用时初始Singleton，以后就不用再生成了。

注意到lazy  initialization形式中的synchronized，这个synchronized很重要，如果没有synchronized，那么使用getInstance()是有可能得到多个Singleton实例。关于lazy  initialization的Singleton有很多涉及double-checked locking (DCL)的讨论，有兴趣者进一步研究。

一般认为第一种形式要更加安全些。

<strong>使用Singleton注意事项</strong>：
有时在某些情况下，使用Singleton并不能达到Singleton的目的，如有多个Singleton对象同时被不同的类装入器装载；在EJB这样的分布式系统中使用也要注意这种情况，因为EJB是跨服务器，跨JVM的。

我们以SUN公司的宠物店源码(Pet Store 1.3.1)的ServiceLocator为例稍微分析一下：

在Pet  Store中ServiceLocator有两种，一个是EJB目录下；一个是WEB目录下，我们检查这两个ServiceLocator会发现内容差不多，都是提供EJB的查询定位服务，可是为什么要分开呢？仔细研究对这两种ServiceLocator才发现区别：在WEB中的ServiceLocator的采取Singleton模式，ServiceLocator属于资源定位，理所当然应该使用Singleton模式。但是在EJB中，Singleton模式已经失去作用，所以ServiceLocator才分成两种，一种面向WEB服务的，一种是面向EJB服务的。

Singleton模式看起来简单，使用方法也很方便，但是真正用好，是非常不容易，需要对Java的类 线程 内存等概念有相当的了解。

总之：如果你的应用基于容器，那么Singleton模式少用或者不用，可以使用相关替代技术。

转自：http://www.jdon.com/designpatterns/singleton.htm
