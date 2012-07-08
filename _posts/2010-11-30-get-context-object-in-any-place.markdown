---
layout: post
title: 在任意位置获取应用程序Context
wordpress_id: 1012
wordpress_url: http://www.hijava.org/?p=1012
date: 2010-11-30 16:08:43.000000000 +08:00
---
Android程序中访问资源时需要提供Context，一般来说只有在各种component中（Activity, Provider等等)才能方便的使用api来获取Context, 而在某些工具类中要获取就很麻烦了。为此，我们可以自定义一个Application类来实现这种功能。
	import android.app.Application;

	public class MyApplication extends Application {
	    private static MyApplication instance;

	    public static MyApplication getInstance() {
		return instance;
	    }

	    @Override
	    public void onCreate() {
		// TODO Auto-generated method stub
		super.onCreate();
		instance = this;
	    }
	}

然后在manifest中中加入name="mypackage.MyApplication"就可以在任意类中使用MyApplication.getInstance()来获取应用程序Context了。

转自：<a href="http://eshock.blogbus.com/logs/65414382.html" target="_blank">http://eshock.blogbus.com/logs/65414382.html</a>
