---
layout: post
title: java获取本机mac地址
wordpress_id: 26
wordpress_url: http://www.hijava.org/?p=26
date: 2008-08-28 21:05:45.000000000 +08:00
---
关键代码如下：
	public static String getMac() throws IOException
	{
		String command="ipconfig /all";
		String mac=null;
		Process proc=Runtime.getRuntime().exec(command);
		BufferedReader reader=new BufferedReader(new InputStreamReader(proc.getInputStream()));
		String line=null;
		while((line=reader.readLine())!=null)
		{
		if(line.indexOf("Physical Address")!=-1)
		{
		mac=line.substring(line.indexOf("Physical Address")+36, line.length());
		break;
		}
		}
		return mac;
	}
