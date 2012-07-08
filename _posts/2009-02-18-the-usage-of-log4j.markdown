---
layout: post
title: Log4j使用
wordpress_id: 169
wordpress_url: http://www.hijava.org/?p=169
date: 2009-02-18 15:32:09.000000000 +08:00
---
	import org.apache.log4j.Logger;
	import org.apache.log4j.PropertyConfigurator;

	public class HelloLog {

		static Logger HelloLogger=Logger.getLogger(HelloLog.class);

		public static void main(String args[])
		{

			PropertyConfigurator.configure("log.properties");

			HelloLogger.debug("debug");
			HelloLogger.info("info");
			HelloLogger.warn("warn");
			HelloLogger.error("error");
			HelloLogger.fatal("fatal");
		}

	}
log.properties配置内容如下：
	 ### set log levels ###
	log4j.rootLogger = info,stdout,file
	log4j.logger.test = info,stdout,file

	### 输出到控制台 ###
	log4j.appender.stdout = org.apache.log4j.ConsoleAppender
	log4j.appender.stdout.Target = System.out
	log4j.appender.stdout.layout = org.apache.log4j.PatternLayout
	log4j.appender.stdout.layout.ConversionPattern =  %d{ABSOLUTE} %5p %c{ 1 }:%L - %m%n

	### 输出到日志文件 ###
	log4j.appender.file = org.apache.log4j.DailyRollingFileAppender
	log4j.appender.file.File = logs/log.log
	log4j.appender.file.Append = true
	log4j.appender.file.layout = org.apache.log4j.PatternLayout
	log4j.appender.file.layout.ConversionPattern = %-d{yyyy-MM-dd HH:mm:ss}  [ %t:%r ] - [ %p ]
