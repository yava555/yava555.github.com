---
layout: post
title: finalize函数详解
wordpress_id: 52
wordpress_url: http://www.hijava.org/?p=52
date: 2008-09-11 09:50:13.000000000 +08:00
---
finalize是位于Object类的一个方法，该方法的访问修饰符为protected，由于所有类为Object的子类，因此用户类很容易访问到这个方法。由于，finalize函数没有自动实现链式调用，我们必须手动的实现，因此finalize函数的最后一个语句通常是super.finalize()。通过这种方式，我们可以实现从下到上实现finalize的调用，即先释放自己的资源，然后再释放父类的资源。

根据Java语言规范，JVM保证调用finalize函数之前，这个对象是不可达的，但是JVM不保证这个函数一定会被调用。另外，规范还保证finalize函数最多运行一次。

很多Java初学者会认为这个方法类似与C++中的析构函数，将很多对象、资源的释放都放在这一函数里面。其实，这不是一种很好的方式。原因有三，其一，GC为了能够支持finalize函数，要对覆盖这个函数的对象作很多附加的工作。其二，在finalize运行完成之后，该对象可能变成可达的，GC还要再检查一次该对象是否是可达的。因此，使用finalize会降低GC的运行性能。其三，由于GC调用finalize的时间是不确定的，因此通过这种方式释放资源也是不确定的。

通常，finalize用于一些不容易控制、并且非常重要资源的释放，例如一些I/O的操作，数据的连接。这些资源的释放对整个应用程序是非常关键的。在这种情况下，程序员应该以通过程序本身管理(包括释放)这些资源为主，以finalize函数释放资源方式为辅，形成一种双保险的管理机制，而不应该仅仅依靠finalize来释放资源。

下面给出一个例子说明，finalize函数被调用以后，仍然可能是可达的，同时也可说明一个对象的finalize只可能运行一次。
	class MyObject{
	    Test main; //记录Test对象，在finalize中时用于恢复可达性
	    public MyObject(Test t)
	    {
		main=t; //保存Test 对象
	    }
	    protected void finalize()
	    {
		main.ref=this;// 恢复本对象，让本对象可达
		System.out.println("This is finalize");//用于测试finalize只运行一次
	    }
	}
	class Test {
		MyObject ref;
	 	public static void main(String[] args) {
	 		Test test=new Test();
	 		test.ref=new MyObject(test);
	 		test.ref=null; //MyObject对象为不可达对象，finalize将被调用
	 		System.gc();
	 		if (test.ref!=null) System.out.println("My Object还活着");
		}
	}
运行结果：
	This is finalize
	MyObject还活着

此例子中，需要注意的是虽然MyObject对象在finalize中变成可达对象，但是下次回收时候，finalize却不再被调用，因为finalize函数最多只调用一次。

摘自：http://www.ibm.com/developerworks/cn/java/l-JavaMemoryLeak2/
