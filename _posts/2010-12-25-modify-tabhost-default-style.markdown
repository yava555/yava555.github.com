---
layout: post
title: 修改TabHost默认样式
wordpress_id: 1043
wordpress_url: http://www.hijava.org/?p=1043
date: 2010-12-25 17:46:47.000000000 +08:00
---
TabHost是Android提供的一个容器组件，利用它可以轻松地实现TAB界面，如下图所示：

<a href="/uploads/2010/12/tabhost.jpg"><img class="alignnone size-full wp-image-1044" title="tabhost" src="/uploads/2010/12/tabhost.jpg" alt="" width="322" height="91" /></a>

但很多时候，默认的TAB样式并不符合软件的整体风格，这时候该怎么办呢？其实，我们可以编写XML对其样式进行修改。下面修改后的效果图：

<a href="/uploads/2010/12/tabhost_1.jpg"><img class="alignnone size-full wp-image-1045" title="tabhost_1" src="/uploads/2010/12/tabhost_1.jpg" alt="" width="318" height="36" /></a>


<h3>1. TabHost布局文件 main.xml</h3>
	<TabHost
	    android:id="@+id/tabhost"  
	    android:layout_width="fill_parent"
	    android:layout_height="fill_parent">  
	    <LinearLayout  
		android:orientation="vertical"
		android:layout_width="fill_parent"  
		android:layout_height="fill_parent">  
		<TabWidget  
		    android:id="@android:id/tabs"
		    android:layout_width="fill_parent" 
		    android:layout_height="30dip"
		    android:background="#a0a0a0"
		    android:layout_weight="0" />  
		<FrameLayout  
		    android:id="@android:id/tabcontent"  
		    android:layout_width="fill_parent"  
		    android:layout_height="fill_parent"
		    android:layout_weight="1">
				  <ListView 
				    android:id="@+id/user_list"
				    android:layout_width="fill_parent"
				    android:layout_height="fill_parent" 
				    android:divider="@drawable/divider_line"
				    android:cacheColorHint="#00000000" />
				  <ListView 
				    android:id="@+id/article_list"
				    android:layout_width="fill_parent"
				    android:layout_height="fill_parent" 
				    android:divider="@drawable/divider_line"
				    android:cacheColorHint="#00000000" />  
				  <ListView 
				    android:id="@+id/feed_list"
				    android:layout_width="fill_parent"
				    android:layout_height="fill_parent" 
				    android:divider="@drawable/divider_line"
				    android:cacheColorHint="#00000000" />  
				  <ListView 
				    android:id="@+id/book_list"
				    android:layout_width="fill_parent"
				    android:layout_height="fill_parent" 
				    android:divider="@drawable/divider_line"
				    android:cacheColorHint="#00000000" />  				    				    				      
		</FrameLayout>  
	    </LinearLayout>  
	</TabHost>
FrameLayout里有四个ListView 分别对应用户、文章、频道、图书。
TabWidget和FrameLayout的ID不能自己定义修改。

<h3>2. Activity后台代码</h3>

	RelativeLayout articleTab = (RelativeLayout) LayoutInflater.from(this).inflate(R.layout.minitab, null);
	TextView articleTabLabel = (TextView) articleTab.findViewById(R.id.tab_label);
	articleTabLabel.setText("文章");

	RelativeLayout feedTab = (RelativeLayout) LayoutInflater.from(this).inflate(R.layout.minitab, null);
	TextView feedTabLabel = (TextView) feedTab.findViewById(R.id.tab_label);
	feedTabLabel.setText("频道");

	RelativeLayout bookTab = (RelativeLayout) LayoutInflater.from(this).inflate(R.layout.minitab, null);
	TextView bookTabLabel = (TextView) bookTab.findViewById(R.id.tab_label);
	bookTabLabel.setText("图书");

	TabHost tabHost = (TabHost) findViewById(R.id.tabhost);
	tabHost.setup();

	tabHost.addTab(tabHost.newTabSpec("user").setIndicator(userTab).setContent(R.id.user_list));
	tabHost.addTab(tabHost.newTabSpec("article").setIndicator(articleTab).setContent(R.id.article_list));
	tabHost.addTab(tabHost.newTabSpec("feed").setIndicator(feedTab).setContent(R.id.feed_list));
	tabHost.addTab(tabHost.newTabSpec("book").setIndicator(bookTab).setContent(R.id.book_list));

TabHost创建出来以后，必须先setup一下，tabHost.setup();
setIndicator方法设置的View其实就对应了TAB中的一个个选项卡，它们都是通过一个叫minitab的布局文件inflate出来的。

<h3>3. 选项卡布局文件minitab.xml</h3>
	<?xml version="1.0" encoding="utf-8"?>
	<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"  
	    android:layout_width="fill_parent"
	    android:layout_height="fill_parent"
	    android:paddingLeft="5dip"
	    android:paddingRight="5dip">  
	    
	    <TextView android:id="@+id/tab_label"  
		android:layout_width="fill_parent"
		android:layout_height="fill_parent"
		android:gravity="center"
		android:textColor="#000000"
		android:textStyle="bold"
		android:background="@drawable/minitab" /> 
	</RelativeLayout>
drawable/minitab是一个selector，指定了Tab选项卡的背景颜色。
<h3>4. selector文件 minitab.xml</h3>
	<?xml version="1.0" encoding="utf-8"?>
	<selector
		xmlns:android="http://schemas.android.com/apk/res/android"
		>
		<item
			android:state_selected="false"
			android:drawable="@drawable/minitab_unselected"
			>
		</item>
		<item
			android:state_selected="true"
			android:drawable="@drawable/minitab_default"
			>
		</item>
	</selector>
minitab_unselected是一浅蓝色背景图片
minitab_default是一白色背景图片
