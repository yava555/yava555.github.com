---
layout: post
title: 如何去掉Android App里的内置广告
wordpress_id: 1109
wordpress_url: http://www.hijava.org/?p=1109
date: 2012-01-01 10:12:23.000000000 +08:00
---
1、使用apktool 工具反编译 myapp.apk文件
<blockquote>apktool d myapp.apk myapp/</blockquote>
2、修改layout文件，找到广告对应的View，将layout_height 与 layout_width 设置成0dip

3、使用apktool 重新打包修改过的源文件
<blockquote>apktool b myapp</blockquote>
新生成的myapp.apk 在myapp/dist目录下

4、使用jarsigner对新生成的apk进行签名
<blockquote>jarsigner -verbose -keystore key.keystore -signedjar myapp_signed.apk myapp.apk passwd</blockquote>
myapp_signed.apk就是去掉广告后的apk文件
