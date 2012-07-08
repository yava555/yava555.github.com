---
layout: post
title: 利用Ant脚本实现Android项目自动批量打包
wordpress_id: 1106
wordpress_url: http://www.hijava.org/?p=1106
date: 2011-06-25 14:50:21.000000000 +08:00
---
因为Android项目加入了有盟统计，每次升级都需要单独针对每一个market或论坛打一个apk，这样当渠道变得越来越多时，打包就变成了一件相当繁琐的事情。

其实可以用Ant脚本来实现自动批量打包：

一、为Android项目增加自定义Ant支持：
这里有一篇非常不错的介绍说明：  
<a href="https://www.readability.com/articles/bpyzsmet" target="_blank">Using Ant to Automate Building Android Applications</a>
<span style="color: #ff0000;">不过有一点不太准确：android_rules模板文件，应该采用android-sdk-windows\tools\ant\main_rules.xml，文章中的android_rules.xml 或 ant_rules_r#.xml都有问题。</span>

二、在build.xml中增加如下代码：
	<taskdef resource="net/sf/antcontrib/antcontrib.properties">
	  <classpath>
		<pathelement location="lib/ant-contrib-1.0b3.jar"/>
	  </classpath>
	</taskdef>
	 
	 
	 <target name="deploy">
	   <foreach target="modify_manifest" list="${market_channels}" param="channel" delimiter=",">
	   </foreach>
	 </target>

	<target name="modify_manifest">
		<replaceregexp flags="g" byline="false">
		<regexp pattern="android:value=&quot;(.*)&quot; android:name=&quot;UMENG_CHANNEL&quot;" />
		<substitution expression="android:value=&quot;${channel}&quot; android:name=&quot;UMENG_CHANNEL&quot;" />
		<fileset dir="" includes="AndroidManifest.xml" />
		</replaceregexp>
		<property name="out.release.file"
					  location="${out.absolute.dir}/${ant.project.name}_${channel}_${app_version}.apk" />
		<antcall target="release" />  
	</target>
taskdef 声明需要放到较前位置，因为if condition也会用到此声明。

build.properties文件增加：
	market_channels=UMENG,XIANGUO,MARKET,HIAPK,GOAPK
	app_version=1.2.1
market名称用逗号分隔

执行ant deploy会自动在项目bin目录下生成如下apk文件：
<a href="/uploads/2011/06/ant-apks.jpg"><img src="/uploads/2011/06/ant-apks-300x152.jpg" alt="" title="ant-apks" width="300" height="152" class="alignnone size-medium wp-image-1107" /></a>
