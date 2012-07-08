---
layout: post
title: 如何在同一Tomcat下进行多端口配置
wordpress_id: 477
wordpress_url: http://www.hijava.org/?p=477
date: 2009-08-24 17:37:21.000000000 +08:00
---
首先来看一下%Tomcat%/conf下的server.xml配置文件：
	<Service name="Catalina">
	    <Connector port="8080" maxHttpHeaderSize="8192"
		       maxThreads="150" minSpareThreads="25" maxSpareThreads="75"
		       enableLookups="false" redirectPort="8443" acceptCount="100"
		       connectionTimeout="20000" disableUploadTimeout="true" />
	    <Connector port="8009" 
		       enableLookups="false" redirectPort="8443" protocol="AJP/1.3" />
	    <Engine name="Catalina" defaultHost="localhost">
	      <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
		     resourceName="UserDatabase"/>
	      <Host name="localhost" appBase="webapps"
	       unpackWARs="true" autoDeploy="true"
	       xmlValidation="false" xmlNamespaceAware="false">
	      </Host>
	    </Engine>
	 </Service>
分别注意下，Service,Engine和Host节点的name属性。再来看一下conf目录下是不是存在Catalina/localhost这样的目录结构，而且host-manager.xml和manager.xml都在此目录下。

看到这里就应该知道该怎么进行多端口配置了吧？在conf目录下创建sample/localhost的目录结构，sample可以随意。然后在server.xml中添加相应的service节点，不要忘记修改端口号。
	<Service name="sample">
	    <Connector port="80" maxHttpHeaderSize="8192"
		       maxThreads="150" minSpareThreads="25" maxSpareThreads="75"
		       enableLookups="false" redirectPort="8453" acceptCount="100"
		       connectionTimeout="20000" disableUploadTimeout="true" />
	    <Connector port="8019" 
		       enableLookups="false" redirectPort="8453" protocol="AJP/1.3" />
	    <Engine name="Qone" defaultHost="localhost">
	      <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
		     resourceName="UserDatabase"/>
	      <Host name="localhost" appBase="webapps"
	       unpackWARs="true" autoDeploy="true"
	       xmlValidation="false" xmlNamespaceAware="false">
	      </Host>
	    </Engine>
	  </Service>
不得不佩服tomcat的扩展性设计。
