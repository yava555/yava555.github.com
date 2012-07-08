---
layout: post
title: ! '[转]Top 10 tools for java development'
wordpress_id: 232
wordpress_url: http://www.hijava.org/?p=232
date: 2009-03-12 20:17:56.000000000 +08:00
---
As a java developer, I am always trying to get someone else to do little jobs for me. Could someone get me a build of the project? Could someone figure out what libraries we are dependent on, and are we using a compatible version? You get the picture. I don’t want to talk specifically about frameworks, as that could be another series of posts entirely. This is a list of tools (and possibly frameworks) that I have found most helpful in any java development I have done.
<ol>
	<li> Eclipse (http://www.eclipse.org) - everyone should know what eclipse is by now. The reason I include it here is mostly due to the refactoring support is immensely helpful.</li>
	<li>Ant (http://ant.apache.org/) - again, everyone should know this tool by now. Ant is a fantastic build tool, but allows you to do much more with all of the extension support. I have seen some very cool things done with ant, ivy and a few custom tasks.</li>
	<li>JUnit (http://junit.org/) - people should know this framework, but many people still don’t subscribe to the automated unit testing model. I find automated unit tests a great way to ensure you haven’t broke anything mainly because I regularly break my own tests.</li>
	<li>Tomcat (http://tomcat.apache.org/) - Tomcat is obviously more useful if you are doing web development in java. Duh. However, if you do any of that and have tried configuring something like WebSphere, you can understand why I include it.</li>
	<li>Sitemesh (http://www.opensymphony.com/sitemesh/) - Sitemesh is one of the simplest web presentation frameworks I have seen. It can be seen as a basic template engine, but quite often that is all that you need. The difficulty with most web frameworks is that they try to be all things to all people. Sitemesh just wants to put a nice configurable template around your content. The idea of “do one thing and do it well” comes to mind.</li>
	<li>Spring (http://www.springframework.org/) - Spring is one of the “web” frameworks that tries to be all things to all people. However, it doesn’t do a bad job. If you are involved with a large project, Spring gives you some nice functionality out of the box without having to go the coding standards route.</li>
	<li>Ivy (http://ant.apache.org/ivy/) - Well, some things have changed in Ivy-land. It is an ant subproject now and soon to be moving to the ant site. This might be a good thing. Ivy is a dependency management tool that can be used with ant. If you have more than one small project, you are likely to need dependency management. I like it because I am not required to move to Maven which I have not had much success with.</li>
	<li>Luntbuild (http://luntbuild.javaforge.com/) - Luntbuild is an open source GUI build management tool. So, you already have your ant builds and they can be integrated with luntbuild. The bonus with luntbuild is that you can have separate development, qa and production configurations for the build. There is also a professional version called quickbuild (http://www.pmease.com/) that comes with support and some additional features.</li>
	<li>Cobertura (http://cobertura.sourceforge.net/) - This is my favorite code coverage tool, mainly because it works and it is free. Code coverage is a good metric to have because it will quickly show you where you have less tests. You will never hit 100% coverage (and you shouldn’t), but it is a good benchmark to look at, especially if you get some defect density numbers from your code as well.</li>
	<li>Xerces (http://xerces.apache.org/) - Is there any other XML parsing library out there?</li>
</ol>
虽然是E文的，但是都是专业词汇，还算比较好理解。有几个工具竟然从来没有听说过，改天再好好研究一下！

转自：<a href="http://regulargeek.com/2007/12/17/top-10-tools-for-java-development/" target="_blank">http://regulargeek.com/2007/12/17/top-10-tools-for-java-development/</a>
