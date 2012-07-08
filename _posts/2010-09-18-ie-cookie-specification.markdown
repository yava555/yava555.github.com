---
layout: post
title: ! '[转]IE Cookie文件格式说明 '
wordpress_id: 946
wordpress_url: http://www.hijava.org/?p=946
date: 2010-09-18 16:09:18.000000000 +08:00
---
<h3>1、Cookie文件的实质</h3>
Cookie实际上是Web服务端与客户端（典型的是浏览器）交互时彼此传递的一部分内容，内容可以是任意的，但要在允许的长度范围之内。客户端会将它保存在本地机器上（如IE便会保存在本地的一个txt文件中），由客户端程序对其进行管理，过期的Cookie会自动删除。每当客户端访问某个域下某个目录中的网页时，便会将保存在本地并且属于那个域下对应目录的有效Cookie信息附在网页请求的头部信息当中一并发送给服务端。
<h3>2、Cookie文件的保存位置</h3>
不同的客户端，其Cookie的保存方式、保存位置各不相同，这里只说一下Windows系统中IE的Cookie文件保存位置。

在Windows 2000/XP系统中，Cookie默认保存在C:\Documents and Settings\\Cookies\目录下（此处的为你登录系统时使用的用户名，在开始－＞运行中输入cookies便可打开该目录），命名规则为@.txt。

与2000/XP不同的是，在Windows 95/98/ME系统中Cookie文件默认是保存在C:\Windows\Cookies\目录下的。
<h3>3、Cookie文件的格式</h3>
IE的Cookie文件实际上就是一个txt文本文件，只不过换行符标记为Unix换行标记（0x0A），由于记事本对Unix换行标记不兼容，打开后内容全在一行看起来不方便，我们可以用EditPlus或UltraEdit-32打开，打开之后，会看到形式如下的内容：
name
value
domain/
1600
1263382784
30020896
452781968
30020892
*
每一行的内容说明：

英文说明：
Line Summary
1 The Variable Name
2 The Value for the Variable
3 The Website of the Cookie’s Owner
4 Optional Flags
5 The Most Significant Integer for Expired Time, in FILETIME Format
6 The Least Significant Integer for Expired Time, in FILETIME Format
7 The Most Significant Integer for Creation Time, in FILETIME Format
8 The Least Significant Integer for Creation Time, in FILETIME Format
9 The Cookie Record Delimiter (a * character)

中文说明：
第一行　Cookie变量名
第二行　Cookie变量值
第三行　该Cookie变量所属域，形如csdn.net/、blog.csdn.net/或blog.csdn.net/lixianlin/
第四行　可选标志
第五行　该Cookie过期时间（FILETIME格式）的高位整数
第六行　该Cookie过期时间（FILETIME格式）的低位整数
第七行　该Cookie创建时间（FILETIME格式）的高位整数
第八行　该Cookie创建时间（FILETIME格式）的低位整数
第九行　Cookie记录分隔符（为一个星号* ）

补充一下，第三行中Cookie变量所属域，如csdn.net/，它是一个根域，也就是一级域，表示该Cookie变量在该根域下的所有目录中的网页都有效，不管访问该域下的哪个目录中的网页，浏览器都会将该Cookie信息附在网页头部信息当中发送给服务端；blog.csdn.net/，是一个二级域，表示该Cookie只对blog这个二级域下目录中的网页有效；blog.csdn.net/lixianlin/，是一个二级域下的目录，只有访问blog这个二级域下lixianlin这个目录中的网页时，才会把该Cookie信息附在请求头部信息当中发送给服务端。需要指出的是csdn.net/和www.csdn.net/并不相同，前者是根域，后者是一个二级域，只是人们习惯了www这样的形式，所以大多数的网站首页都用http://www.xxx.com/这样的二级域来访问。

附FILETIME格式定义：
typedef struct _FILETIME {
DWORD dwLowDateTime;
DWORD dwHighDateTime;
} FILETIME, *PFILETIME, *LPFILETIME;

转自：<a href="http://blog.csdn.net/lixianlin/archive/2008/07/30/2738229.aspx" target="_blank">http://blog.csdn.net/lixianlin/archive/2008/07/30/2738229.aspx</a>
