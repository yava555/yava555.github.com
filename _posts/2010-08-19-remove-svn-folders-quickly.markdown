---
layout: post
title: 快速删除.svn文件夹
wordpress_id: 935
date: 2010-08-19 22:20:29.000000000 +08:00
---
采用SVN进行版本控制的项目，会在每一个文件夹下.svn隐藏目录，用来存放一些“meta数据”。有的时候需要将这些svn数据清除掉，最简单的操作方式当然就是查找-删除，但是当项目比较庞大的时候，就会非常耗时，有时候竟会导致系统假死。

从网上搜索了一下，找到了两种比较不错的解决方式：

<strong>Windows系统：</strong>
	Windows Registry Editor Version 5.00

	[HKEY_LOCAL_MACHINE\SOFTWARE\Classes\Folder\shell\DeleteSVN]
	@="Delete SVN Folders"

	[HKEY_LOCAL_MACHINE\SOFTWARE\Classes\Folder\shell\DeleteSVN\command]
	@="cmd.exe /c \"TITLE Removing SVN Folders in %1 && COLOR 9A && FOR /r \"%1\" %%f IN (.svn) DO RD /s /q \"%%f\" \""

将上述代码保存到一个文本文件中，扩展名改成.reg，然后双击运行，导入到注册表中。成功后，在每一个文件夹上点击右键都会有一个“Delete SVN Folders”的选项，点击之后，就可以删除这个文件下下面所有的.svn文件了。

<strong>Linux系统：</strong>
	find . -type d -name ".svn"|xargs rm -rf
在Console中执行上述命令。
