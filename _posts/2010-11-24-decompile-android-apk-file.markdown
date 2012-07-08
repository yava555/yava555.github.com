---
layout: post
title: 【转】反编译Android APK文件
wordpress_id: 974
wordpress_url: http://www.hijava.org/?p=974
date: 2010-11-24 20:37:37.000000000 +08:00
---
<h3>一、<strong>所需工具(点击各自连接进入下载页面)：</strong></h3>
<ol>
	<li><a href="http://code.google.com/p/android4me/downloads/list" target="_blank">AXMLPrinter2.jar</a></li>
	<li><a href="http://code.google.com/p/dex2jar/downloads/list" target="_blank">dex2jar：</a></li>
	<li><a href="http://java.decompiler.free.fr/?q=jdgui" target="_blank">查看Jar包的GUI工具</a></li>
</ol>
<h3>二、开始行动</h3>
<strong>1、用AXMLPrinter2.jar查看apk中的布局xml文件:</strong>

将apk文件(为了方便起见放到tools目录里)用WinRAR等工具打开，将res/layout/main.xml解压出来(也还是放在tools目录里哦)

打开main.xml文件，内容如下(一堆天文):

<a href="/uploads/2010/11/1.jpg"><img class="alignnone size-full wp-image-978" title="1" src="/uploads/2010/11/1.jpg" alt="" width="500" height="236" /></a>

这时候AXMLPrinter2.jar派上用场了，打开cmd终端，一直进入到tools目录下，输入如下命令:

<strong>java -jar AXMLPrinter2.jar main.xml &gt; main.txt.</strong> (如下图所示)

<a href="/uploads/2010/11/2.jpg"><img class="alignnone size-full wp-image-979" title="2" src="/uploads/2010/11/2.jpg" alt="" width="500" height="123" /></a>

打开main.txt代码如下：
	<?xml version="1.0" encoding="utf-8"?>  
	<LinearLayout  
	xmlns:android="http://schemas.android.com/apk/res/android"  
	android:orientation="1"  
	android:layout_width="-1"  
	android:layout_height="-1"  
	>  
	<WebView  
	   android:id="@7F050000"  
	   android:layout_width="-1"  
	   android:layout_height="-2"  
	>  
	</WebView>  
	</LinearLayout> 
为了比对打开源程序中的main.xml代码如下(大家比对一下吧):
	<?xml version="1.0" encoding="utf-8"?>  
	<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"  
	android:orientation="vertical"  
	android:layout_width="fill_parent"  
	android:layout_height="fill_parent"  
	>  
	<WebView  
	android:id="@+id/apk_web"  
	android:layout_height="wrap_content"  
	android:layout_width="fill_parent"  
	/>  
	</LinearLayout>  
<strong>2：通过dex2jar工具进行反编译。</strong>

把apk中的class.dex拷贝到dex2jar.bat所在目录。运行dex2jar.bat   class.dex，将会在其文件夹下生成classes.dex.dex2jar.jar。

<a href="/uploads/2010/11/3.jpg"><img class="alignnone size-full wp-image-980" title="3" src="/uploads/2010/11/3.jpg" alt="" width="500" height="359" /></a>

<strong>3、运行JD-GUI打开生成的classes.dex.dex2jar.jar</strong>

JD-GUI是一个反编译工具，利用它可以得到JAR包的源代码。

<a href="/uploads/2010/11/4.jpg"><img class="alignnone size-full wp-image-981" title="4" src="/uploads/2010/11/4.jpg" alt="" width="500" height="417" /></a>

转自：<a href="http://www.cnblogs.com/stulife/archive/2010/08/24/1807143.html" target="_blank">http://www.cnblogs.com/stulife/archive/2010/08/24/1807143.html</a>

另一篇不错的文章：<a href="http://lytsing.org/wiki/android/decompile.html" target="_blank">http://lytsing.org/wiki/android/decompile.html</a>
