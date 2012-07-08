---
layout: post
title: Java与模式读书笔记-面向对象设计原则
wordpress_id: 444
wordpress_url: http://www.hijava.org/?p=444
date: 2009-07-05 11:20:03.000000000 +08:00
---
<strong>开-闭原则</strong>，Software entities should be open for extension,but closed for modification. 一个软件实体应当对扩展开放，对修改关闭。在设计一个模块的时候，应当使这个模块可以在不被修改的前提下被扩展。换言之，应当可以在不修改源代码的情况下改变这个模块的行为。

<strong>里氏代换原则</strong>，任何基类可以出现的地方，子类一定可以出现。

<strong>依赖倒转原则</strong>，要依赖于抽象，不要依赖于实现。

<strong>合成/聚合复用原则</strong>，要尽量使用合成/聚合，而不是继承关系达到复用的目的。

<strong>迪米特法则</strong>，一个软件实体应当与尽可能少的其他实体发生相互作用。如果系统的模块是相对孤立的，那么它们就不会将修改的压力传递给其他的模块。

<strong>接口隔离原则</strong>，应当为客户端尽可能小的单独的接口，而不要提供大的总接口。
