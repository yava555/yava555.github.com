---
layout: post
title: ! '[转]ubuntu下安装JDK'
wordpress_id: 98
wordpress_url: http://www.hijava.org/?p=98
date: 2008-11-02 11:20:21.000000000 +08:00
---
1、安装jdk1.5 java开源，对于桌面程序的性能提高的很显著。
（1）从sun下载jdk-1_5_0_10-linux-i586.bin

（2）默认的安装目录是/opt/jdk1.6.0
mv ./jdk-1_5_0_10-linux-i586.bin /opt/

（3）
chmod u+x jdk-1_5_0_10-linux-i586.bin

sudo ./jdk-1_5_0_10-linux-i586.bin

或者直接执行：

sh ./jdk-1_5_0_10-linux-i586.bin

选择yes安装

（4）配置classpath，修改所有用户的环境变量

sudo gedit /etc/profile

在文件最后添加
#set java environment
JAVA_HOME=/opt/jdk1.5.0_10
export JRE_HOME=/opt/jdk1.5.0_10/jre
export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH

(5)重新启动，用命令测试jdk的版本
java -version

如果出现
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_10-b03)
Java HotSpot(TM) Client VM (build 1.5.0_10-b03, mixed mode, sharing)
则表示安装成功
