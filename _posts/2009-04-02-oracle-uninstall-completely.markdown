---
layout: post
title: ! '[转]oracle完全卸载'
wordpress_id: 280
wordpress_url: http://www.hijava.org/?p=280
date: 2009-04-02 10:22:53.000000000 +08:00
---
一、Linux 平台Linux 平台下卸载Oracle 非常简单，即：删除Oracle安装目录下的所有文件和文件夹即可。

二、Windows 平台
<ol>
	<li>关闭oracle所有的服务。可以在windows的服务管理器中关闭；</li>
	<li> 打开注册表：regedit 打开路径：
<strong>HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\</strong>
删除该路径下的所有以<strong>oracle</strong>开始的服务名称，这个键是标识Oracle在windows下注册的各种服务！</li>
	<li>打开注册表，找到路径：
<strong>HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE</strong> 删除该oracle目录，该目录下注册着Oracle数据库的软件安装信息。</li>
	<li>删除注册的oracle事件日志，打开注册表
<strong>HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Eventlog\Application</strong> 删除注册表的以oracle开头的所有项目。</li>
	<li>删除环境变量path中关于oracle的内容。</li>
	<li>重新启动操作系统。</li>
</ol>
转自：<a href="http://blog.csdn.net/oceanaut/archive/2009/02/04/3863222.aspx" target="_blank">http://blog.csdn.net/oceanaut/archive/2009/02/04/3863222.aspx</a>
