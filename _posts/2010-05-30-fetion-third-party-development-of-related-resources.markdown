---
layout: post
title: ! '[转]飞信第三方开发相关资源'
wordpress_id: 763
wordpress_url: http://www.hijava.org/?p=763
date: 2010-05-30 11:34:15.000000000 +08:00
---
<h4>一、飞信的第三方程序和开发库</h4>
<h4>LibFetion</h4>
作者：邓东东
网址：<a href="http://www.libfetion.org/">http://www.libfetion.org/</a>
下载： <a title="http://web.libfetion.org/demoapp_download.php" href="http://web.libfetion.org/demoapp_download.php">http://web.libfetion.org/demoapp_download.php</a>
说明：
这个不用说了，第三方飞信中做的最好的。开发很早，用c语言编写，现在各个平台都推出了LibFetion的版本。也就是LibFetion,让我们在 Linux上面终于用上了飞信。官方说LibFetion是一个飞信的开发包，事实上作者只发布了linux下面的开发库，没有发布Windows下的开 发库，这让想开发基于飞信的应用变得比较困难。（这也是促使我写MapleFetion的原因。）因为作者考虑到如果LibFetion大规模的被滥用可 能会被移动封杀，而且有个隐私的问题。
<h4>Fetion.php (OpenFetion)</h4>
作者：youngc527
网址：<a href="http://openfetion.sourceforge.net/">http://openfetion.sourceforge.net</a>
下载： <a title="http://ishare.iask.sina.com.cn/f/7215569.html" href="http://ishare.iask.sina.com.cn/f/7215569.html">http://ishare.iask.sina.com.cn/f/7215569.html</a>
说明：
这是个牛人用PHP写的一个PHP的版飞信。最初发布在SourceForge上面。由于飞信官方调整，现在SF上面下载的暂时登陆不了，请下载修改后的 PHP飞信。实现了登陆飞信，获取好友列表，发送短信的功能。PHP最大的硬伤是不支持线程，无法用一个线程读取数据另外一个线程处理数据，只能使用飞信 的HTTP通信模式。而且PHP脚本执行时间有限制，所以这个PHP脚本只能登陆成功然后发送一条短信就退出了。如果需要用这个ＰＨＰ版的飞信做一个自己 的应用，一定要注意PHP脚本超时的问题。
<h4>PyFetion</h4>
作者：cocobear.cn
网址：<a href="http://code.google.com/p/pytool/">http://code.google.com/p/pytool/</a>
下载：<a href="http://pytool.googlecode.com/files/PyFetion.zip">http://pytool.googlecode.com/files/PyFetion.zip</a>
说明：
用Python写的一个飞信，很简洁，很好用，能添加删除好友，发送短信等。应该是Python版本中比较好的飞信客户端了。
<h4>MiniFetion</h4>
作者：毕飞  Email:175444525@QQ.COM
网址： 无
下载： <a title="http://ishare.iask.sina.com.cn/f/7215489.html" href="http://ishare.iask.sina.com.cn/f/7215489.html">http://ishare.iask.sina.com.cn/f/7215489.html</a>
说明：
这是我在群里发现的一个用VC写的飞信。我使用了一下能够正常登录，发送短信。基于MFC写的。简单的看了下，使用的2008的协议，v1登录，sha验 证，如果需要用MFC写飞信的可以研究下。
<h4>HaozesFx</h4>
作者：Haozes Haozes@gmail.com
网址：<a href="http://haozesfx.codeplex.com/">http://haozesfx.codeplex.com/</a>
下载：
<a href="http://download.codeplex.com/Project/Download/SourceControlFileDownload.ashx?ProjectName=HaozesFx&amp;changeSetId=42766">http://download.codeplex.com/Project/Download/SourceControlFileDownload.ashx?ProjectName=HaozesFx&amp;changeSetId=42766</a>
说明：
这应该是一个飞信的机器人，作者完整的写了一个飞信客户端的实现，用C#写的，基于2008的协议，并基于这个飞信客户端，实现了一个飞信机器人，可以用 你的飞信帐号登陆,发短信或者用飞信IM与之交互,执行精灵命令或计划任务。作者代码写得很好，值得学习一下。程序运行能登录成功，但双击弹出界面的时候 会崩溃，我C#不太懂，没查出原因，那位高手可以帮忙检查一下。
<h4>MilyFx</h4>
作者：echo.xjtu
网址：<a href="http://code.google.com/p/milyfx/">http://code.google.com/p/milyfx/</a>
下载： <a href="http://milyfx.googlecode.com/files/MilyFX_v0.0.2.7z">http://milyfx.googlecode.com/files/MilyFX_v0.0.2.7z</a>
说明：
这个是基于LibFetion开发的一个命令行的飞信，现在已经不能正常登录了，我本来想修改一下的，但把最新的LibFetion库文件导入之后编译一 大堆的错误，一下子就没信心了。这里写出来就是想给那些想用LibFetion开发应用的朋友给个例子，希望有所帮助。
<h4>飞信机器人</h4>
作者：常堂主 shichangguo@msn.com
网址：<a href="http://www.it-adv.net/">http://www.it-adv.net/</a>
下载：<a title="http://ishare.iask.sina.com.cn/f/7215532.html" href="http://ishare.iask.sina.com.cn/f/7215532.html">http://ishare.iask.sina.com.cn/f/7215532.html</a>
说明：
也是一个人独立开发的飞信应用，没有使用LibFetion库，用C语言写的，实现的飞信的基本功能，可以使用命令行发送短信添加好友等操作。遗憾的不是 开源的。自带了一套机器人框架，使用PHP做脚本，便于开发和扩展。现在的官网已经找不到这套机器人框架的下载了，不过我在Googlecode找到了作 者托管的机器人框架，找到了数据字典，总算完整了，就是里面的实例没了，如果有兴趣的可以参照官网的开发文档独立的开发。
<h4>MapleFetion</h4>
作者：solosky <a href="http://www.solosky.net/">http://www.solosky.net</a>
网址：<a href="http://maplefetion.googlecode.com/">http://maplefetion.googlecode.com</a>
下载： <a href="http://maplefetion.googlecode.com/files/MapleFetion-1.0-Beta3.zip">http://maplefetion.googlecode.com/files/MapleFetion-1.0-Beta3.zip</a>
说明：
这个是我参照Nathan的分析和自己抓包分析，独立写出的飞信开发包，使用JAVA作为开发语言，实现了飞信的基本功能。可能是现在网上功能最完整的开 发包了。我的目标是做一个完整的飞信开发库，希望能让大家能利用飞信做一些好的应用，不要做一些非法的事情。现在代码库里已经是MapleFetion  2.0的版本了，预计在不久的将来就会发布beta1了。正在逐步完善中。。
<h4>二、WEB飞信接口</h4>
WEB飞信接口只需通过一个URL就可以发送手机短信给指定的用户，使用很方便，但账号安全性得不到保证，如果只是简单的发送一条短信还是可以是用 ＷＥＢ接口的，毕竟这样简单的需求很多。如果对这些第三方的接口安全性有疑虑的话，可以采用上面开源或者部分开源的飞信开发库赖实现自己的应用。
<h4>sms.api.bz</h4>
网址：<a href="http://sms.api.bz/">http://sms.api.bz/</a>
作者：张宴 <a href="http://blog.s135.com/fetion_api/">http://blog.s135.com/fetion_api/</a>
说明：
很简单的接口，支持HTTP和HTTPS。
<h4>fetionapi.appspot.com</h4>
网址：<a href="https://fetionapi.appspot.com/">https://fetionapi.appspot.com/</a>
作者：gohsy
说明：
部署在ＧoogleAppEngine上面的一个飞信ＷＥＢ接口，也实现了基本的功能。仅支持HTTPS模式。但放在GAE上的，有被GFW被墙的危险。
<h4>io2.139icq.com （原www.feirobot.cn/）</h4>
网址：<a href="http://io2.139icq.com:88/fWebSer.asmx">http://io2.139icq.com:88/fWebSer.asmx</a>
作者：未知（QQ：14334655）
说明：
这是一个WebService接口，飞信接口后台服务程序有引用飞信客户端的DLL文件，调用正常编程引用所能看到的相关类及函数来实现飞信的操作，应该 是比较稳定的一个飞信接口。
<h4>三、WEB飞信</h4>
WEB飞信是直接在网页上登录飞信。可以很方便在不用下载飞信客户端登录发送短信，十分方便。当然同样也有账号安全的问题，请各位慎用。
<h4>fetionlib.appspot.com</h4>
网址：<a href="https://fetionlib.appspot.com/">https://fetionlib.appspot.com/</a>
作者：Terry <a href="http://xinghuo.org.ru/">http://xinghuo.org.ru/</a>
说明：
做的很好的一个WEB飞信，同样部署在GAE上面。界面很简洁。
<h4>四、WAP飞信</h4>
<em> </em> WAP飞信可以让没有JAVA扩展功能的手机用上飞信，只要能上网的手机都可以用，如果你是聊天狂人或者是正在热恋，合理的使用ＷＡＰ飞信可以减少不少的 短信费用哦。
<h4>wap.maYax.cn</h4>
网址：wap://wap.mayax.cn （只能用ＷＡＰ访问，可以用http://w.159.com/来浏览）
作者：Mayax
说明：
mayax应该是很早就在做WAP的飞信了，因为最开始研究飞信就是mayax指点的，感谢mayax。现在mayax的飞信比较成熟，鼓励大家都去使用 哈。
<h4>五、一些飞信的分析工具和资源</h4>
这些仅给那些愿意从头开始分析飞信的朋友，敬佩并看好这些愿意分析飞信的朋友，愿意研究说明你很想知道飞信的实现原理，要钻研才会有进步，希望你们 一定要保持一种好奇心，相信你们研究完飞信，自己能力有了一个质的提高。
<h4>飞信分析工具</h4>
网址：<a href="http://hi.baidu.com/nathan2007/blog/item/1b65521e027211f51ad57676.html">http://hi.baidu.com/nathan2007/blog/item/1b65521e027211f51ad57676.html</a>
作者：nathan2007 <a href="http://hi.baidu.com/nathan2007">http://hi.baidu.com/nathan2007</a>
下载：<a href="http://pickup.mofile.com/3783779038816952">http://pickup.mofile.com/3783779038816952</a>
说明：
这个是nathan写的分析工具。其实里面还有一些其他工具，如配置编辑，感觉没啥用。主要是FetionSniffer.exe，用winCap写的抓 包工具，很方便。注意使用之前一定要安装包里的wincap组件。然后要编辑FetionSniffer.config，在里面填上你那个地方飞信服务器 的地址（不同的地方地址不一样），不然啥也抓不到。
<h4>Reflector 反编译工具</h4>
网址：<a href="http://www.red-gate.com/products/reflector/">http://www.red-gate.com/products/reflector/</a>
作者：Lutz Roeder
下载：<a href="http://reflector.red-gate.com/download.aspx">http://reflector.red-gate.com/download.aspx</a>
说明：
这个很好很强大。可以反编译C#编译之后的文件，可以看到源代码级别的飞信代码。分析飞信就完全靠他了。因为飞信是C#写的，使用这个工具，就直接可以看 到飞信的源代码，没有解决不了的问题。
<h4>手机飞信反编译版本</h4>
网址：无
作者：飞信官方
下载： <a title="http://ishare.iask.sina.com.cn/f/7215532.html" href="http://ishare.iask.sina.com.cn/f/7215532.html">http://ishare.iask.sina.com.cn/f/7215532.html</a>
说明：
这是是手机飞信用JD反编译出来的代码。不是symbian版的，是JAVA版的，应该是最先的那个版本，要求最低，只要在支持JAVA的手机上都可以使 用。目前还可以使用，如果有朋友对手机版的飞信有兴趣可以研究研究。
<h4>天网防火墙</h4>
网址：<a href="http://pfw.sky.net.cn/">http://pfw.sky.net.cn/</a>
作者：广州众达天网技术有限公司
下载： <a title="http://ishare.iask.sina.com.cn/f/7215694.html" href="http://ishare.iask.sina.com.cn/f/7215694.html">http://ishare.iask.sina.com.cn/f/7215694.html</a>
说明：
分析网络软件少不了防火墙，因为配置好防火墙可以模拟特定的网络状态。比如要研究飞信的HTTP通信协议，就需要把阻止飞信连接8080端口，用防火墙可 以办到。这里我给的是破解版的防火墙，因为天网很久不更新这个防火墙了，不过的确很好用。
<h4>六、网络资源</h4>
<strong> </strong>目前飞信程序一大堆，但真正分析并写文章的少，这里只能列出一点来，希望研究飞信的朋友们能写出更多关于飞信 的文章。
<h4>nathan2007的博客</h4>
网址：<a href="http://hi.baidu.com/nathan2007">http://hi.baidu.com/nathan2007</a>
作者：nathan2007
说明：
nathan2007应该是最早分析飞信的人了，我也是看完nathan2007的分析才开始研究飞信的。文章比较丰富，但是有些内容在新版的飞信已经不 适用了。
<h4>solosky的博客</h4>
网址：<a href="http://www.solosky.net/">http://www.solosky.net</a>
作者：solosky <a href="mailto:solosky772@qq.com">solosky772@qq.com</a>

转自：<a href="http://www.solosky.net/2010/03/the-fetion-resources.html" target="_blank">http://www.solosky.net/2010/03/the-fetion-resources.html</a>
