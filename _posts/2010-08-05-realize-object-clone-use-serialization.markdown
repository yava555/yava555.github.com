---
layout: post
title: 利用序列化实现Java对象深度clone
wordpress_id: 837
wordpress_url: http://www.hijava.org/?p=837
date: 2010-08-05 13:27:05.000000000 +08:00
---
对于简单的对象，只要实现Cloneable接口，并且重写Object类的clone()方法即可。对于复杂的对象，必需将其中的复杂成员变量也进行clone，实现起来太繁琐。这里有一种简便方法，先将对象序列化到内存，然后再其反序列化。主要代码如下所示：
	ByteArrayOutputStream  byteOut = new ByteArrayOutputStream();
	ObjectOutputStream out = new ObjectOutputStream(byteOut);
	out.writeObject(obj);
	ByteArrayInputStream byteIn = new ByteArrayInputStream(byteOut.toByteArray());
	ObjectInputStream in =new ObjectInputStream(byteIn);
	Object newObj=in.readObject();

参照：<a href="http://lovelace.javaeye.com/blog/182772" target="_blank">java clone方法使用详解</a>
