---
layout: post
title: Cygwin下Vim设置
wordpress_id: 216
wordpress_url: http://www.hijava.org/?p=216
date: 2009-03-04 20:13:28.000000000 +08:00
---
今天在Cygwin下安装上Vim后发现BackSpace键无法正常使用，经过搜索发现，可以在Vim中使用以下两条命令解决：

<code>set nocompatible
set backspace=2</code>

但是，不能每次打开Vim，都要敲入上述命令吧？最后终于发现完美的解决方法：

在/usr/share/vim/vim72中，手动创建.vimrc文件：
<code>$ cd /usr/share/vim/vim72
$ cp vimrc_example.vim .vimrc</code>
