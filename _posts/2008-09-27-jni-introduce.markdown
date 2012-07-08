---
layout: post
title: JNI介绍
wordpress_id: 83
wordpress_url: http://www.hijava.org/?p=83
date: 2008-09-27 12:51:55.000000000 +08:00
---
JNI是Java Native Interface的缩写。从Java 1.1开始，Java Native Interface (JNI)标准成为java平台的一部分，它允许Java代码和其他语言写的代码进行交互。JNI一开始是为了本地已编译语言，尤其是C和C++而设计的，但是它并不妨碍你使用其他语言，只要调用约定受支持就可以了。

使用java与本地已编译的代码交互，通常会丧失平台可移植性。但是，有些情况下这样做是可以接受的，甚至是必须的，比如，使用一些旧的库，与硬件、操作系统进行交互，或者为了提高程序的性能。JNI标准至少保证本地代码能工作在任何Java 虚拟机实现下。

摘自：http://baike.baidu.com/view/1272329.htm
