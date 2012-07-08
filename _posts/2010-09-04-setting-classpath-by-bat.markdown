---
layout: post
title: 通过批处理设置CLASSPATH
wordpress_id: 943
wordpress_url: http://www.hijava.org/?p=943
date: 2010-09-04 15:46:34.000000000 +08:00
---
	@echo off & setlocal EnableDelayedExpansion
	set LIB_CP=
	for /r . %%i in ("lib\*.jar") do (
		set LIB_CP=!LIB_CP!;%%i
	)
	java -cp .\conf%LIB_CP%
	exporting.gui.ExportWizard

可以将某个目录下的所有JAR文件配置到环境变量中，很强大的一段脚本～
