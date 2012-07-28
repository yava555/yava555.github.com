---
layout: post
title: Sublime Text2
date: 2012-07-28 14:17:22.000000000 +08:00
categories:
- 技术
tags:
- sublime text

---

使用了一上午Sublime Text2，发现果然是一神器，完全超乎了我的想象。以前还担心转到Mac OS X后找不到Source Insight的替代品，现在看来完全是多虑了。

关于Sublime Text的介绍，@lucifr写了一系列详尽的文章，见这里：[http://lucifr.com/tags/sublime-text/](http://lucifr.com/tags/sublime-text/)。在这里我只是记录一下我的配置过程：


### 安装[Sublime Package Control](http://wbond.net/sublime_packages/package_control)

*ctrl+` 调出控制台，然后在控制台中执行如下命令：*

	import urllib2,os; pf='Package Control.sublime-package'; ipp=sublime.installed_packages_path(); os.makedirs(ipp) if not os.path.exists(ipp) else None; urllib2.install_opener(urllib2.build_opener(urllib2.ProxyHandler())); open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read()); print 'Please restart Sublime Text to finish installation'
	
	
### 安装[Ctags](https://github.com/SublimeText/CTags)，用于变量方法定义跳转

- 快捷键“Ctrl+Shift+P”打开命令面板，选择“Package Control : Install Package”，搜索Ctags进行安装
- 用终端在项目路径下执行*ctags -R -f .tags*，用于生成.tags文件
- 重新打开Sublime，将光标停在某个变量或方法名称上，“Ctrl＋Alt＋]”快捷键就能跳到变量或方法定义的位置，“Ctrl＋Alt＋[”返回调用前位置


### 安装Gist插件，作为代码片段管理器
快捷键“Ctrl+Shift+P”打开命令面板，选择“Package Control : Install Package”，搜索Gist进行安装
安装完后在Tools菜单下有一个Gist子菜单，可以将选则的代码片段保存到GitHub Gist上。


### 修改快捷键，Settings-User设置内容如下（还在慢慢完善中...）：
	[
		{"keys": ["super+j"], "command": "navigate_to_definition"},
		{"keys": ["super+shift+j"], "command": "jump_back"},
		{ "keys": ["super+k"], "command": "find_under" },
		{ "keys": ["super+shift+k"], "command": "find_under_prev" }

	]
command+k往下查找选取关键词，command+shift+k往上查找  
command+j跳转到定义位置，command+shift+j返回 < 覆盖了Ctrl+Alt+] 和 Ctrl+Alt+[ >



