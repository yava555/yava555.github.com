---
layout: post
title: Java集合排序方法
wordpress_id: 531
wordpress_url: http://www.hijava.org/?p=531
date: 2010-02-06 20:28:21.000000000 +08:00
---
前一段时间写过的一个集合排序的方法，可以按照集合中存放Bean的任意属性进行排序。

	/**
	 * 按照指定属性，对List集合进行排序。
	 * 
	 * @param list bean集合
	 * @param sortBy 要进行排序的bean中的属性
	 * @param sort 升序或降序
	 */
	public static <T> void sort(List<T> list, final String sortBy,final String sort)  {
		if (list == null || sortBy == null ||sortBy.equals("")|| list.isEmpty())
			return;
		Collections.sort(list, new Comparator<T>() {
			@SuppressWarnings("unchecked")
			public int compare(T t1, T t2) {
				Object o1 = null;
				Object o2 = null;
				try {
					o1 = ReflexUtil.getObjFieldValue(t1, sortBy);
					o2 = ReflexUtil.getObjFieldValue(t2, sortBy);
				} catch (Exception e) {
					e.printStackTrace();
				}
				int result = 0;
				if(o1==null){
					result=-1;
				}
				else if(o2==null){
					result=1;
				}
				//字符串按照拼音排序
				else if (o1 instanceof String) {
					result = Collator.getInstance(Locale.CHINA).compare(o1, o2);
				} else {
					result = ((Comparable) o1).compareTo(o2);
				}
			
				if(DESC.equalsIgnoreCase(sort)){
					result=0-result;
				}
				return result;

			}
		});

	}

注：ReflexUtil.getObjFieldValue(t1, sortBy) 用反射技术获取对象t1中sortBy属性的值。
