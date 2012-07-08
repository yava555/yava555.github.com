---
layout: post
title: Java(Rome)生成RSS
wordpress_id: 434
wordpress_url: http://www.hijava.org/?p=434
date: 2009-06-27 17:00:35.000000000 +08:00
---
用到了<a href="https://rome.dev.java.net/">Rome</a>组件包，另外还需要用到jdom.jar
	<%@ page language="java" import="java.util.*,org.hijava.entity.*,org.hijava.dao.*" pageEncoding="UTF-8"%>
	<%@ page import="com.sun.syndication.feed.synd.*,com.sun.syndication.io.*" >
	<%@ page import="java.text.*" %>
	<%
		String basePath=request.getScheme()+"://"+request.getServerName()+":"+request.getServerPort()+request.getContextPath()+"/";
		response.setContentType("text/xml; charset=UTF-8");

		Setting setting=(Setting)application.getAttribute("setting");
		int feed_num=setting.getFeed_num();

		List articles=ArticleDao.getArticles(feed_num);

		SyndFeed feed = new SyndFeedImpl();
		feed.setFeedType("rss_2.0");//指定RSS版本
		feed.setTitle(setting.getBlog_name());
		feed.setLink(basePath+"index.jsp");
		feed.setDescription(setting.getBlog_desc());

		List entries=new ArrayList();
		SimpleDateFormat sdf=new SimpleDateFormat("yyyy/MM/dd");

		for(Article article : articles){
		SyndEntry entry=new SyndEntryImpl();
		SyndContent content=new SyndContentImpl();

		entry.setTitle(article.getPost_title());
		entry.setLink(basePath+"single.jsp?id="+article.getPost_id());
		entry.setPublishedDate(sdf.parse(article.getPost_date()));
		entry.setAuthor(article.getUser_name());

		content.setType("text/plain");
		content.setValue(article.getPost_content());
		entry.setDescription(content);

		entries.add(entry);
		}
		feed.setEntries(entries);
		SyndFeedOutput put=new SyndFeedOutput();
		put.output(feed,response.getWriter());
	 %>
