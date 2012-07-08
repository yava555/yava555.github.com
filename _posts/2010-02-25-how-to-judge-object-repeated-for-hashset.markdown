---
layout: post
title: HashSet中是如何判断元素是否重复的
wordpress_id: 547
wordpress_url: http://www.hijava.org/?p=547
date: 2010-02-25 23:43:02.000000000 +08:00
---
今天工作中遇到一个问题，虽然在Employee中重写了equals方法，但是往HashSet中存放Employee对象的时候还是出现了重复值。

于是查看了JDK源码，发现HashSet竟然是借助HashMap来实现的，利用HashMap中Key的唯一性，来保证HashSet中不出现重复值。具体参见代码：

	public class HashSet<E>
	    extends AbstractSet<E>
	    implements Set<E>, Cloneable, java.io.Serializable
	{
	    private transient HashMap<E,Object> map;

	    // Dummy value to associate with an Object in the backing Map
	    private static final Object PRESENT = new Object();

	    public HashSet() {
		map = new HashMap<E,Object>();
	    }

	    public boolean contains(Object o) {
		return map.containsKey(o);
	    }

	    public boolean add(E e) {
		return map.put(e, PRESENT)==null;
	    }
	}


由此可见，HashSet中的元素实际上是作为HashMap中的Key存放在HashMap中的。下面是HashMap类中的put方法：

	public V put(K key, V value) {
		if (key == null)
		    return putForNullKey(value);
		int hash = hash(key.hashCode());
		int i = indexFor(hash, table.length);
		for (Entry<K,V> e = table[i]; e != null; e = e.next) {
		    Object k;
		    if (e.hash == hash && ((k = e.key) == key || key.equals(k))) {
			V oldValue = e.value;
			e.value = value;
			e.recordAccess(this);
			return oldValue;
		    }
		}
	}

从这段代码中可以看出，HashMap中的Key是根据对象的hashCode() 和 euqals()来判断是否唯一的。

<strong>结论：</strong>为了保证HashSet中的对象不会出现重复值，在被存放元素的类中必须要重写hashCode()和equals()这两个方法。
