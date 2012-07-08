---
layout: post
title: Ubuntu下笔记本休眠或挂起无法唤醒的解决办法
wordpress_id: 504
wordpress_url: http://www.hijava.org/?p=504
date: 2009-11-05 22:14:28.000000000 +08:00
---
当初用ubuntu6.06的时候，基本上是不敢用挂起功能的。因为一般情况下，挂起了之后90%是不能唤醒的，现在换到了7.04之后，这个挂起功能好了不少，基本上和原来调个个了，基本上90%都能唤醒，但是时常还是有那10%不能唤醒。

最近仔细了解了一下laptop_mode，发现只要打开laptop_mode，Laptop挂起之后无法唤醒的问题已经就不存在了。

<span style="color: #0000ff;"><strong>关于laptop_mode</strong></span>
在默认情况下，你通过安装完系统到笔记本上后，就安装上了laptop-mode-tools工具包。如果你不缺认自已是否安装了laptop-mode-tools工具包，可以在终端中输入下列命令来确认是否安装。

<code>dpkg -l | grep laptop-mode-tools</code>

如果你的电脑执行命今后无结果输出，那么你可以通过下列命令来安装。

<code>sudo  apt-get install laptop-mode-tools</code>

虽然系统已自动安装了laptop-mode-tools，但是是不是就自动启动了laptop_mode模式了呢？我们用下列命令来判断Laptop是否启用了laptop_mode，如果显示结果为0，则表示未启动，如果为非0的数字则表示启动了。

<code>cat /proc/sys/vm/laptop_mode</code>

怎样启动laptop_mode模式呢？
1.修改配置文件/etc/default/acpi-support，更改ENABLE_LAPTOP_MODE=true

<code>sudo gedit /etc/default/acpi-support</code>

2.然后在默认情况下UBUNTU系统会在你切换电源到电池供电时启动laptop_mode，如果你现在就想启动laptop_mode模式，请直接在终端中输入

<code>sudo laptop_mode start|stop|restart</code>

启动了laptop_mode之后，在ubuntu挂起后，基本上就不会遇到无法唤醒的情况了。

转自: <a href="http://www.oceanboo.cn/read.php/82.htm" target="_blank">http://www.oceanboo.cn/read.php/82.htm</a>
