---
layout: post
title: 十进制转十六进制（c语言实现）
wordpress_id: 208
wordpress_url: http://www.hijava.org/?p=208
date: 2009-02-27 20:24:13.000000000 +08:00
---
	#includ<stdio.h>

	int main()
	{
		char str[]={'0','1','2','3','4','5','6','7','8','9','A','B','C','D','E','F'};
		char data[100];
		printf("Input a number:\n");
		int n,m,i=0;
		scanf("%d",&n);

		while(n!=0)
		{
			m=n &amp; 0xf;
			data[i]=str[m];
			n=n &gt;&gt; 4;
			i++;
		}
		data[i]='\0';

		for(--i;i>=0;i--)
		{
			printf("%c",data[i]);
		}
		printf("\n");
		return 0;
	}
其中不得不提的是，m=n & 0xf（除16取余）n=n >> 4（除16取商，右移4位），这样能够提高程序的执行效率，面试经常被问到的问题。
