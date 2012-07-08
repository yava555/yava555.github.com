---
layout: post
title: HttpBot网络爬虫
wordpress_id: 812
wordpress_url: http://www.hijava.org/?p=812
date: 2010-08-01 23:43:19.000000000 +08:00
---
<blockquote>HttpBot 是对 java.net.HttpURLConnection类的简单封装，可以方便的获取网页内容，并且自动管理session，自动处理301重定向等。虽然不能像HttpClient那样强大，支持完整的Http协议，但却非常地灵活，可以满足我目前所有的相关需求。</blockquote>
获取Google首页Html代码仅需要如下两行代码即可：
	HttpBot httpBot=new HttpBot();
	String html=httpBot.doGet("http://www.google.com");
感兴趣的可以到 <em>http://hijava.googlecode.com/svn/HttpBot</em> (SVN地址) 下载最新的源码。目前还太简单（200行代码），不过仍在不断维护中。

HttpBot部分源代码：
	package org.hijava.httpbot;

	import java.io.BufferedReader;
	import java.io.IOException;
	import java.io.InputStream;
	import java.io.InputStreamReader;
	import java.io.OutputStream;
	import java.io.UnsupportedEncodingException;
	import java.net.HttpURLConnection;
	import java.net.URL;
	import java.net.URLEncoder;
	import java.util.HashMap;
	import java.util.Map;

	/**
	 * Http网络爬虫类
	 *
	 * @author yava
	 */
	public class HttpBot {
		private Map cookieMap;
		private String userAgent;
		private String encoding;
		private String host;
		private String referer;
		private int responseCode;
		private static final String separator = System.getProperty("line.separator");
		private static final String GET="GET";
		private static final String POST="POST";

		public HttpBot() {
			this.userAgent = "Mozilla/5.0 (Windows; U; Windows NT 5.1; zh-CN; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5";
			this.encoding = "UTF-8";
			cookieMap=new HashMap();
		}

		public HttpBot(String host,String referer){
			this();
			this.host=host;
			this.referer=referer;
		}
		/**
		 * 以GET方式发送请求，返回页面html代码
		 * @param urlStr
		 * @return
		 */
		public String doGet(String urlStr) {
			HttpURLConnection http=getConnection(urlStr,HttpBot.GET);
			String content="";
			try {
				http.connect();
				processCookie(http);
				this.referer=urlStr;
				this.responseCode=http.getResponseCode();
				if(this.responseCode==302){
					String location=http.getHeaderField("Location");
					return doGet(location);
				}
				InputStream is=http.getInputStream();
				content=getContent(is);
				is.close();
				http.disconnect();
			} catch (IOException e) {
				e.printStackTrace();
			}
			return content;
		}
		/**
		 * 以Post方式发送请求，返回页面html代码
		 * @param urlStr
		 * @param paramMap 请求参数
		 * @return
		 */
		public String doPost(String urlStr,Map paramMap){
			HttpURLConnection http=getConnection(urlStr,HttpBot.POST);
			http.setDoOutput(true);
			String content="";
			try {
				OutputStream os = http.getOutputStream();
				os.write(getParamBytes(paramMap));
				http.connect();
				processCookie(http);
				this.referer=urlStr;
				this.responseCode=http.getResponseCode();
				if(this.responseCode==302){
					String location=http.getHeaderField("Location");
					return doGet(location);
				}
				InputStream is=http.getInputStream();
				content=getContent(is);
				is.close();
				http.disconnect();
			} catch (IOException e) {
				e.printStackTrace();
			}
			return content;
		}
		/**
		 * 从输入流获取网页内容
		 * @param is
		 * @return
		 */
		private String getContent(InputStream is){
			StringBuilder builder = new StringBuilder();
			try {
				BufferedReader reader = new BufferedReader(new InputStreamReader(is,encoding));
				String line;
				while ((line = reader.readLine()) != null) {
					builder.append(line).append(separator);
				}
			} catch (UnsupportedEncodingException e) {
				e.printStackTrace();
			} catch (IOException e) {
				e.printStackTrace();
			}

			return builder.toString();
		}

		private HttpURLConnection getConnection(String urlStr,String reqMethod){
			HttpURLConnection http=null;
			try {
				URL url = new URL(urlStr);
				http = (HttpURLConnection) url.openConnection();
				http.setRequestProperty("User-Agent", this.userAgent);
				http.setRequestProperty("Host", this.host);
				http.setRequestProperty("Cookie", this.getCookie());
				http.setRequestProperty("Referer", this.referer);
				http.setRequestMethod(reqMethod);
				http.setInstanceFollowRedirects(false);
			} catch (IOException e) {
				e.printStackTrace();
			}

			return http;
		}
		/**
		 * 处理cookie
		 * @param http
		 */
		private void processCookie(HttpURLConnection http){
			String key = null;
			for (int i = 1; (key = http.getHeaderFieldKey(i)) != null; i++) {
				if (key.equalsIgnoreCase("set-cookie")) {
					String cookie = null;
					cookie = http.getHeaderField(i);
					int i1=cookie.indexOf("=");
					int i2=cookie.indexOf(";");
					if(i1!=-1&amp;&amp;i2!=-1){
						String _value=cookie.substring(i1+1, i2);
						if("EXPIRED".equalsIgnoreCase(_value)){
							continue;
						}
						String _key=cookie.substring(0, i1);
						cookieMap.put(_key, _value);
					}
				}
			}
		}
		/**
		 * 获取cookie
		 * @return
		 */
		public String getCookie(){
			String cookie="";
			for(Map.Entry entry:cookieMap.entrySet()){
				cookie=cookie+entry.getKey()+"="+entry.getValue()+";";
			}
			return cookie;
		}

		private byte[] getParamBytes(Map paramMap){
			String paramStr="";
			for(Map.Entry entry:paramMap.entrySet()){
				String value="";
				try {
					value=URLEncoder.encode(entry.getValue(), "UTF-8");
				} catch (UnsupportedEncodingException e) {
					e.printStackTrace();
				}
				paramStr=paramStr+entry.getKey()+"="+value+"&amp;";
			}
			return paramStr.getBytes();
		}
	}
