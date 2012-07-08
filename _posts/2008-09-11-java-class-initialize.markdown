---
layout: post
title: Java类初始化顺序
wordpress_id: 43
wordpress_url: http://www.hijava.org/?p=43
date: 2008-09-11 08:44:16.000000000 +08:00
---
1、类只有在使用New调用创建的时候才会被JAVA类装载器装入
2、JAVA类首次装入时，会对静态成员变量或方法进行一次初始化,但方法不被调用是不会执行的，静态成员变量和静态初始化块级别相同，非静态成员变量和非静态初始化块级别相同。
先初始化父类的静态代码---&gt;初始化子类的静态代码--&gt;
初始化父类的非静态代码---&gt;初始化父类构造函数---&gt;
初始化子类非静态代码---&gt;初始化子类构造函数
3、创建类实例时，首先按照父子继承关系进行初始化
4、类实例创建时候，首先初始化块部分先执行，然后是构造方法；然后从
本类继承的子类的初始化块执行，最后是子类的构造方法
5、类消除时候，首先消除子类部分，再消除父类部分
	public class A {

		public A() {
			System.out.println("A");
		}

		static {
			System.out.println("Static A");
		}

	}
	public class B extends A {

		public B() {
			System.out.println("B");
		}

		static {
			System.out.println("Static B");
		}

	}
	public class test {

		public static void main(String[] args) {
			A a = new B();
			a = new B();
		}

	}
执行结果是：
	Static A
	Static B
	A
	B
	A
	B
