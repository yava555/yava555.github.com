---
layout: post
title: ! '[转]拥抱Android：快速预览'
wordpress_id: 792
wordpress_url: http://www.hijava.org/?p=792
date: 2010-07-06 21:27:01.000000000 +08:00
---
自从Google发起开发<a href="http://www.android.com/">Android OS</a>迄今已有三年，这是它在互  联网世界取得巨大成功后，旨在称霸竞争激烈的移动互联世界而挥出的一记重拳。 <a href="http://en.wikipedia.org/wiki/Android_os">Android</a>是专为移动设备开发的操  作系统，里面包括了中间件平台和一些核心程序。  然而，它并不只限于智能手机使用，它可以用在平板电脑、电子阅读设备、甚至上网本上。       掀开它的面纱，你会发现其实里面竟是个Linux内核。在它诞生之初，只有不多的一些设备支持它，其中第一个就是2008年十月发布的<a href="http://en.wikipedia.org/wiki/HTC_Dream">HTC Dream</a>。 至此之后，<a href="http://en.wikipedia.org/wiki/List_of_Android_devices">支持  Android的设备</a>迅速增长。

Google已将大部分的Android代码发布于Apache软件许可协议下。Apache软件许可协议被公认为“企业友好”的许可证，它允许厂 商扩展 具有专利性质的程序，而不必将扩展的程序提交回开源社区。      你可以直接下载<a href="http://source.android.com/">Android     源代码</a>，把它编译成自己的系统，并在其上运行 Android软件程序。     或者，如果你愿意，花点时间改动它一下。

Google并不是单枪匹马来开发这个复杂的系统。<a href="http://www.openhandsetalliance.com/">Open   Handset Alliance (OHA)</a>已经成立，      它由65家公司组成的企业联盟，旨在为移动设备制定一套开放标准(Google当然首当其冲)。      很多大公司都在列，包括HTC，英特尔，摩托罗拉，Qualcomm， Texas       Instruments，三星，LG，T-Mobile等等。

OHA的<a href="http://www.openhandsetalliance.com/android_overview.html">宗 旨</a>是 制定一个开放的平台，彻底改变当今移动世界的操作模式。  Andorid系统上“所有软件生来平等”的原则给软件的创作带来了活力。   这个原则意味着手机的核心程序和第三方程序享有平等的权利访问手机的各种功能。

如果你是个开发人员，想去<a href="http://developer.android.com/index.html">开发 Android      OS上的软件</a>，那么你需要<a href="http://developer.android.com/sdk/index.html">Android     SDK</a>。Android  SDK由一套很复杂的开发工具组成。它支持所有的主要操作平台(Windows,      Mac, Linux)。 而开发软件使用的主要语言是…  Java。     然而，这些开发出的软件并不是在普通的Java虚拟机上运行，而是在一个为Andorid     特别设计的虚拟机上运行，叫做<a href="http://en.wikipedia.org/wiki/Dalvik_virtual_machine">Dalvik</a>，它 为 只有有限的内存和CPU的电池供电的移动设备进行了专门的优化。所以说，它跟JME一定关系都没有，完全不同的一套系统。 这使得使用Java  SE和ME编写的Java程序和Android平台上编写的程序出现不兼容性。 Android只是使用了Java语言的语法定义，它只支持提供Java  SE和ME里的部分类库和API。

如果你认为程序性能是头等大事，那你需要<a href="http://developer.android.com/sdk/ndk/index.html">Android     NDK</a>， 它是Android SDK的一个附加工具，可以使Android程序开发人员把他们的跟性能最相关的部分代码编译成本地代码。

Dalvik虚拟机上运行的程序一般都被打包成Dalvik(.dex)可执行格式，这些程序适合在那些内存和处理器受限制的系统上运行。  如果你想对Dalvik虚拟机做深入研究，请查看<a href="http://sites.google.com/site/io/dalvik-vm-internals">Dalvik内部结构说明书</a>。   从Android 2.2 版本后， Dalvik提供了一个<a href="http://en.wikipedia.org/wiki/Just-in-time_compilation">即时编译器</a>，它  能使程序的执行效率大大提高。  跟大多数虚拟机上的代码一样，Dalvik上也有一个.DEX文件反编译器，叫做<a href="http://dedexer.sourceforge.net/">Dedexer</a>，同样也是个开源软件。

我们必须要注意一点，Dalvik其实是使用      Apache的Harmony项目的一个子集作为其核心<a href="http://en.wikipedia.org/wiki/Java_Class_Library">类库</a>的。<a href="http://en.wikipedia.org/wiki/Apache_Harmony">Apache Harmony</a>是一个  开源的、免费版的Java语言实现,它实现了Java SE 5      和 6的规范。就像在其<a href="http://harmony.apache.org/">网站上</a>说明的一样，     这个项目的主要目的是提供：
<ul>
	<li>在Apache 许可证 v2 下的一个兼容的、独立的Java SE 5 JDK实现。</li>
</ul>
<ul>
	<li>一个由社区组织开发的、模块化的运行时虚拟机和类库</li>
</ul>
为了吸引全世界的人们去为它的新操作系统开发应用程序，Google组织了一系列<a href="http://en.wikipedia.org/wiki/Android_Developer_Challenge">Android开  发者挑战赛</a>，这是一场最有创新性的Android应用程序竞赛。还有什么比提供一万千美元的奖励还能鼓舞开发人员的吗？其中有两个挑战赛吸引了 全 世界开发者的注意。  点击下面的链接查看获胜者的信息：
<ul>
	<li><a href="http://code.google.com/android/adc/adc_gallery/">Android开  发者挑战赛前五十强</a></li>
	<li><a href="http://code.google.com/android/adc/gallery_winners.html">Android  开发者挑战赛2所有获胜者</a></li>
</ul>
新开发出的Android应用程序，不管是免费的还是商业的，你都可以从<a href="http://www.android.com/market/">Android     市场</a>找到。      Android市场是一个Google开发的在线的软件库。     它提供了一个分类目录，你可以把上面的应用程序通过<a href="http://en.wikipedia.org/wiki/Over-the-air_programming">在线方式</a>下载安  装到你的目标设备上，而不需要使用PC机。  Android市场增长迅速，目前上面已经驻留了超过70,000个应用软件(截至2010年六月)。你自己可以看一下<a href="http://www.androlib.com/appstats.aspx">市场统计</a>。

Android目前的版本号是Froyo，此版本做了很多的改进，加入了很多<a href="http://smarterware.org/6085/android-2-2-screenshot-tour-my-favorite-features-in-froyo">新  功能</a>。 当然，<a href="http://android-developers.blogspot.com/2010/05/android-22-and-developers-goodies.html">开  发人员们</a>使用的SDK和NDK也有了很多的改进。

这就是我要介绍的，一个对移动平台的简单介绍。在随后的几篇文章里，我们将会讲解如何在虚拟机里安装Android   OS，告诉你如何使用SDK开发Android应用程序。

转自：<a href="http://www.aqee.net/2010/07/06/embracing-the-android-awesomeness-a-quick-overview/" target="_blank">http://www.aqee.net/2010/07/06/embracing-the-android-awesomeness-a-quick-overview/</a>
