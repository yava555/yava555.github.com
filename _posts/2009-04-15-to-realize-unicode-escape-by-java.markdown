---
layout: post
title: 用Java来实现字符串Unicode转义
wordpress_id: 329
wordpress_url: http://www.hijava.org/?p=329
date: 2009-04-15 21:54:46.000000000 +08:00
---
关键代码如下：

	String s = "欢迎=welcome";
	char charArray[] = s.toCharArray();
	for (char c : charArray) {
		if(c>=0&&c<=127)
		{
			System.out.print(c);//英文ACSII，直接输出
		}
		else
		{
			System.out.print("\\u"+Integer.toHexString(c));
		}
	}

输出结果为：
	\u6b22\u8fce=welcome

可以用native2ascii.exe转换工具，测试一下结果。
