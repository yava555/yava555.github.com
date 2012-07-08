---
layout: post
title: 修改MyEclipse中的Jsp页面模板
wordpress_id: 171
wordpress_url: http://www.hijava.org/?p=171
date: 2009-02-19 09:21:31.000000000 +08:00
---
每次用MyEclipse新建Jsp页面，都要删除一些无用的代码，修改pageEncoding. 今天从网上搜索了一下修改Jsp页面模本的方法：找到MyEclipse安装路径下的myeclipse\eclipse\plugins\com.genuitec.eclipse.wizards_6.6.0.zmyeclipse660200810\（我用的是MyEclipse6.6，具体路径可能根据版本略有不同），修改templates\jsp\Jsp.vtl即可。如果要增加模板，需要先修改templates.xml文件，然后在templates目录下增加模板文件。
