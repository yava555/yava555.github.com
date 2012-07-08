---
layout: post
title: 如何改变Android Progressbar默认颜色
wordpress_id: 1080
wordpress_url: http://www.hijava.org/?p=1080
date: 2011-06-18 20:53:34.000000000 +08:00
---
默认情况下Indeterminate Progressbar是白色的，如果容器的背景也是白色的，这样就根本看不到Progressbar了。

幸好Android自带了一些反转样式，你可以采用其中一个合适的：

	<ProgressBar style="@android:style/Widget.ProgressBar.Inverse"/>
	<ProgressBar style="@android:style/Widget.ProgressBar.Large.Inverse"/>
	<ProgressBar style="@android:style/Widget.ProgressBar.Small.Inverse"/>

转自：<a href="http://stackoverflow.com/questions/2638161/how-to-change-android-indeterminate-progressbar-color" target="_blank">http://stackoverflow.com/questions/2638161/how-to-change-android-indeterminate-progressbar-color</a>
