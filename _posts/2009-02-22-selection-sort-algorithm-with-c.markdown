---
layout: post
title: 选择排序算法（c语言实现）
wordpress_id: 196
wordpress_url: http://www.hijava.org/?p=196
date: 2009-02-22 20:53:57.000000000 +08:00
---
关键代码如下：
	void selection_sort(int list[], int n)
	{
	   int i, j, min;

	   for (i = 0; i < n - 1; i++)
	   {
	     min = i;
	     for (j = i+1; j < n; j++)
	     {
		if (list[j] < list[min])
		{
		   min = j;
		}
	     }
	     swap(&list[i], &list[min]);
	   }
	}
