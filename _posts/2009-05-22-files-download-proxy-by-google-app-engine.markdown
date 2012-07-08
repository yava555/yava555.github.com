---
layout: post
title: 利用GAE做文件下载代理
wordpress_id: 407
wordpress_url: http://www.hijava.org/?p=407
date: 2009-05-22 14:47:34.000000000 +08:00
---
由于培训基地的网络做了限制，导致一些文件不能下载，造成了很大的困扰。今天突然有了一个利用Google服务器代理文件下载的想法。关键代码如下：
	String urlStr=req.getParameter("url");
	String filename=urlStr.substring(urlStr.lastIndexOf("/")+1);
	resp.setContentType("application/x-download");
	resp.addHeader("Content-Disposition","attachment;filename=" + java.net.URLEncoder.encode(filename,"UTF-8")); 

	URL url=new URL(urlStr);
	HttpURLConnection http=(HttpURLConnection) url.openConnection();
	http.setRequestProperty("User-Agent", "Mozilla/5.0 (Windows; U; Windows NT 5.1; zh-CN; rv:1.9.0.8) Gecko/2009032609 Firefox/3.0.8 (.NET CLR 3.5.30729)");

	InputStream is=http.getInputStream();
	byte[] data=new byte[500];
	int n=is.read(data);
	OutputStream out=resp.getOutputStream();
	while(n&gt;0){
		out.write(data,0,n);
		n=is.read(data);
	}
	is.close();
	out.close();
主要是利用HttpURLConnection 获取要下载的文件，然后再将获得的字节流输出。注意：下载大一点的文件时会抛出“ResponseTooLargeException”，估计可能是GAE限制，知道如何解决这个问题的朋友，可以给我留言。
