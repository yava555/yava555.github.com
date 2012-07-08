---
layout: post
title: ADB常用命令
wordpress_id: 999
wordpress_url: http://www.hijava.org/?p=999
date: 2010-11-26 19:30:54.000000000 +08:00
---
<img class="alignnone size-full wp-image-1009" title="android_avatar" src="/uploads/2010/11/android_avatar.png" alt="" width="94" height="94" />
<blockquote>ADB(Android Debug Bridge)是Android SDK中里的一个工具，用它可以控制和调试你的Android设备或模拟器。</blockquote>
下面是几个常用的命令：
<ol>
	<li>查看所有连接的设备：<strong>adb devices</strong></li>
	<li>拷贝本地文件到设备：<strong>adb push &lt;local&gt; &lt;remote&gt;</strong></li>
	<li>拷贝设备里文件到本地：<strong>adb pull &lt;remote&gt; &lt;local&gt;</strong></li>
	<li>进入linux shell：<strong>adb shell</strong></li>
	<li>查看log日志：<strong>adb logcat</strong></li>
	<li>安装应用程序到设备：<strong>adb install [-l] [-r] &lt;file&gt;</strong></li>
	<li>卸载设备里的应用程序：<strong> adb uninstall [-k] &lt;package&gt;</strong></li>
</ol>
PS. 如果同时连接多个设备或模拟器，执行上述命令时，会报“error: more than one device and emulator” ，这时需要加 -s 参数，例如：<strong>adb -s emulator-5554 shell</strong>

注："emulator-5554"是设备名称，可执行<strong>adb devices</strong>命令查看。

详情：<a href="http://android-dls.com/wiki/index.php?title=ADB" target="_blank">http://android-dls.com/wiki/index.php?title=ADB</a>
