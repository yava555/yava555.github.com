---
layout: post
title: ! '[转]深入理解abstract和interface'
wordpress_id: 75
wordpress_url: http://www.hijava.org/?p=75
date: 2008-09-19 09:20:38.000000000 +08:00
---
<blockquote>
<div>abstract  class和interface是Java语言中对于抽象类定义进行支持的两种机制，正是由于这两种机制的存在，才赋予了Java强大的面向对象能力。abstract  class和interface之间在对于抽象类定义的支持方面具有很大的相似性，甚至可以相互替换，因此很多开发者在进行抽象类定义时对于abstract  class和interface的选择显得比较随意。其实，两者之间还是有很大的区别的，对于它们的选择甚至反映出对于问题领域本质的理解、对于设计意图的理解是否正确、合理。本文将对它们之间的区别进行一番剖析，试图给开发者提供一个在二者之间进行选择的依据。</div></blockquote>
<div><strong><span class="atitle2">异同：</span></strong></div>
<div><strong></strong></div>
<div><span class="atitle2">1、abstract class首先是一个class，其子类继承他的同时不能再继承其他abstract  class。</span></div>
<div><span class="atitle2">2、abstract class可以有方法体，甚至可以有构造方法，但是不能实例化。</span></div>
<div><span class="atitle2">3、abstract  class和interface虽然本身都不能实例化，但是其实现类或者子类能实例化他。</span></div>
<div><span class="atitle2">4、interface中不能有static方法，只能存在public或者abstract方法。</span></div>
<div><strong><span class="atitle2">理解抽象类</span></strong></div>
abstract class和interface在Java语言中都是用来进行抽象类（本文中的抽象类并非从abstract  class翻译而来，它表示的是一个抽象体，而abstract  class为Java语言中用于定义抽象类的一种方法，请读者注意区分）定义的，那么什么是抽象类，使用抽象类能为我们带来什么好处呢？

在面向对象的概念中，我们知道所有的对象都是通过类来描绘的，但是反过来却不是这样。并不是所有的类都是用来描绘对象的，如果一个类中没有包含足够的信息来描绘一个具体的对象，这样的类就是抽象类。抽象类往往用来表征我们在对问题领域进行分析、设计中得出的抽象概念，是对一系列看上去不同，但是本质上相同的具体概念的抽象。比如：如果我们进行一个图形编辑软件的开发，就会发现问题领域存在着圆、三角形这样一些具体概念，它们是不同的，但是它们又都属于形状这样一个概念，形状这个概念在问题领域是不存在的，它就是一个抽象概念。正是因为抽象的概念在问题领域没有对应的具体概念，所以用以表征抽象概念的抽象类是不能够实例化的。
<div>在面向对象领域，抽象类主要用来进行类型隐藏。我们可以构造出一个固定的一组行为的抽象描述，但是这组行为却能够有任意个可能的具体实现方式。这个抽象描述就是抽象类，而这一组任意个可能的具体实现则表现为所有可能的派生类。模块可以操作一个抽象体。由于模块依赖于一个固定的抽象体，因此它可以是不允许修改的；同时，通过从这个抽象体派生，也可扩展此模块的行为功能。熟悉OCP的读者一定知道，为了能够实现面向对象设计的一个最核心的原则OCP(<strong>Open-Closed  Principle</strong>)，抽象类是其中的关键所在。</div>
在abstract  class方式中，Demo可以有自己的数据成员，也可以有非abstarct的成员方法，而在interface方式的实现中，Demo只能够有静态的不能被修改的数据成员（也就是必须是static  final的，不过在interface中一般不定义数据成员），所有的成员方法都是abstract的。从某种意义上说，interface是一种特殊形式的abstract  class。

对于abstract  class和interface在语法定义层面更多的细节问题，不是本文的重点，不再赘述，读者可以参阅参考文献〔1〕获得更多的相关内容。

<strong><span class="atitle2">从编程层面看abstract class和interface</span></strong>

从编程的角度来看，abstract class和interface都可以用来实现"design by  contract"的思想。但是在具体的使用上面还是有一些区别的。

首先，abstract  class在Java语言中表示的是一种继承关系，一个类只能使用一次继承关系。但是，一个类却可以实现多个interface。也许，这是Java语言的设计者在考虑Java对于多重继承的支持方面的一种折中考虑吧。

其次，在abstract  class的定义中，我们可以赋予方法的默认行为。但是在interface的定义中，方法却不能拥有默认行为，为了绕过这个限制，必须使用委托，但是这会  增加一些复杂性，有时会造成很大的麻烦。

在抽象类中不能定义默认行为还存在另一个比较严重的问题，那就是可能会造成维护上的麻烦。因为如果后来想修改类的界面（一般通过abstract  class或者interface来表示）以适应新的情况（比如，添加新的方法或者给已用的方法中添加新的参数）时，就会非常的麻烦，可能要花费很多的时间（对于派生类很多的情况，尤为如此）。但是如果界面是通过abstract  class来实现的，那么可能就只需要修改定义在abstract class中的默认行为就可以了。

同样，如果不能在抽象类中定义默认行为，就会导致同样的方法实现出现在该抽象类的每一个派生类中，违反了"one rule，one  place"原则，造成代码重复，同样不利于以后的维护。因此，在abstract class和interface间进行选择时要非常的小心。

<strong><span class="atitle2">从设计理念层面看abstract class和interface</span></strong>

上面主要从语法定义和编程的角度论述了abstract  class和interface的区别，这些层面的区别是比较低层次的、非本质的。本小节将从另一个层面：abstract  class和interface所反映出的设计理念，来分析一下二者的区别。作者认为，从这个层面进行分析才能理解二者概念的本质所在。
<div>前面已经提到过，abstarct class在Java语言中体现了一种继承关系，要想使得继承关系合理，父类和派生类之间必须存在"is  a"关系，即父类和派生类在概念本质上应该是相同的（参考文献〔3〕中有关于"is a"关系的大篇幅深入的论述，有兴趣的读者可以参考）。对于interface  来说则不然，并不要求interface的实现者和interface定义在概念本质上是一致的，仅仅是实现了interface定义的契约而已。为了使论述便于理解，下面将通过一个简单的实例进行说明。</div>
<div>

<strong><span class="atitle2">结论</span></strong>

abstract  class和interface是Java语言中的两种定义抽象类的方式，它们之间有很大的相似性。但是对于它们的选择却又往往反映出对于问题领域中的概念本质的理解、对于设计意图的反映是否正确、合理，因为它们表现了概念间的不同的关系（虽然都能够实现需求的功能）。这其实也是语言的一种的惯用法，希望读者朋友能够细细体会

转自：http://www.blog.sh/u4/wealupa/79320.html</div>
