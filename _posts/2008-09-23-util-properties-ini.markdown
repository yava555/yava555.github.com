---
layout: post
title: 利用java.util.Properties读取ini配置文件
wordpress_id: 79
wordpress_url: http://www.hijava.org/?p=79
date: 2008-09-23 09:20:04.000000000 +08:00
---
关键代码如下：
	public void getOption() {

		String OptionFile = "Option.ini";

		Properties p = new Properties();
		try {
			p.load(new FileInputStream(OptionFile));
		} catch (FileNotFoundException e) {

			e.printStackTrace();
		} catch (IOException e) {

			e.printStackTrace();
		}
		String Thread_num = p.getProperty("thread_num");
		String Pass_num = p.getProperty("pass_num");
		String Interval_time = p.getProperty("interval_time");

	}
Option.ini文件内容：
	[option]
	thread_num=2
	pass_num=6
	interval_time=6000
