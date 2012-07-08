---
layout: post
title: 快速排序算法（c语言实现）
wordpress_id: 173
wordpress_url: http://www.hijava.org/?p=173
date: 2009-02-22 18:17:10.000000000 +08:00
---
关键代码如下：
	 public void quicksort(int list[],int m,int n)
	 {
		int key,i,j,k;
		if( m < n)
		{
		   k = choose_pivot(m,n);
		   swap(&list[m],&list[k]);
		   key = list[m];
		   i = m+1;
		   j = n;
		   while(i &lt;= j)
		   {
			  while((i &lt;= n) && (list[i] <= key))
					 i++;
			  while((j &gt;= m) && (list[j] > key))
					 j--;
			  if( i < j)
					 swap(&list[i],&list[j]);
		   }

		   swap(&list[m],&list[j]);
		   quicksort(list,m,j-1);
		   quicksort(list,j+1,n);
		}
	 }
原文：<a href="http://cprogramminglanguage.net/quicksort-algorithm-c-source-code.aspx" target="_blank">http://cprogramminglanguage.net/quicksort-algorithm-c-source-code.aspx</a>
