---
layout: post
title: 使用PreparedStatement的好处
wordpress_id: 343
wordpress_url: http://www.hijava.org/?p=343
date: 2009-04-23 10:14:30.000000000 +08:00
---
使用 PreparedStatement

人们认为 PreparedStatement 对象的效率比多个 Statement 对象更高，尤其是如果您必须多次执行同一条语句而差别仅在于参数不同时更是如此。 PreparedStatement 允许您将 SQL 语句“编译”一次（尽管这种编译第一次要消耗较多的时间），然后将它保存在高速缓存中，从而实现有效的重用。同时它也提供了可读性更好的代码。

另一个额外的优势是由驱动程序完成的对用户传递给语句的字符串的自动转义。举例来说，这意味着当您试图将字符串“D'Marco”插入到一个基于字符的数据域（它可能是 VARCHAR, VARCHAR2, CHAR 等）中时，SQL 语句不会在遇到第一个撇号时就产生灾难性的失败。

使用 PreparedStatement 对象时的另一个良好习惯是调用对象自身的 close() 方法来“关闭对象”，这个方法将被用来运行 SQL 语句。这会关闭任何与正在执行的 SQL 语句相关联的游标，这样就能防止打开的游标把数据库弄得十分凌乱。

转自：<a href="http://http://www.ibm.com/developerworks/cn/java/wi-tip28/">http://www.ibm.com/developerworks/cn/java/wi-tip28/</a>
