---
layout: post
title: 自动更改Android项目包名
date: 2012-07-25 22:08:22.000000000 +08:00
categories:
- 技术
tags:
- android
- shell

---

*写了一段Shell脚本用于更改Android项目包名：*

	#!/bin/bash

	old_package_name="com.xianguo.pad"
	new_package_name="com.xianguo.play"

	cd ..

	find . -name "*.java" | xargs sed -i -e "s/${old_package_name}/${new_package_name}/g"
	find . -name "*.xml" | xargs sed -i -e "s/${old_package_name}/${new_package_name}/g"
	find . -name "*.cfg" | xargs sed -i -e "s/${old_package_name}/${new_package_name}/g"
	find . -name "*.html" | xargs sed -i -e "s/${old_package_name}/${new_package_name}/g"

	mv src/${old_package_name//./\/} src/${new_package_name//./\/}
