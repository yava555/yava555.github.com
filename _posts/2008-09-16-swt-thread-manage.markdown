---
layout: post
title: SWT线程管理
wordpress_id: 68
wordpress_url: http://www.hijava.org/?p=68
date: 2008-09-16 08:44:36.000000000 +08:00
---
UI对象由Display对象负责管理，是SWT程序运行的核心。如果在非UI线程中调用界面上的控件对象是会在运行期间报错，所以Display对象使用asyncExec(Runnable runnable)和sysncExec(Runnable runnable)更新界面上的控件对象。
