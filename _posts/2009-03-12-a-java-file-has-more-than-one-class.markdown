---
layout: post
title: 一个文件中包含多个Java类的情况
wordpress_id: 234
wordpress_url: http://www.hijava.org/?p=234
date: 2009-03-12 22:32:48.000000000 +08:00
---
同一个java文件中只能有一个public修饰的类（内部类除外），且文件名应以public类的类名命名。例如下述代码就能通过编译：
	/*
	 * A.java
	 */
	public class A {

	}

	class B {

		public static void main(String[] args) {

			System.out.println("B");
		}
	}
如果把A.java改成B.java就不能通过编译了，编译器会提示：“类 A 是公共的，应在名为 A.java 的文件中声明”。

如果把类B改成public的，同样也不能通过编译，会提示：“类 B 是公共的，应在名为 B.java 的文件中声明”。
