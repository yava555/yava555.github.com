---
layout: post
title: Android单元测试初探
wordpress_id: 1014
wordpress_url: http://www.hijava.org/?p=1014
date: 2010-12-02 17:22:27.000000000 +08:00
---
Android提供了一组强大的测试工具，它针对Android的具体特征对Junit进行了扩展。下面就具体说一下，如何在Android开发环境中引入单元测试。
<h3>1、修改AndroidManifest.xml</h3>
添加<instrumentation> 和 <uses-library android:name="android.test.runner" > 元素，如下所示：
	<application android:icon="@drawable/icon" android:label="@string/app_name">
		<uses-library android:name="android.test.runner" />
	</application>
	<instrumentation android:targetPackage="com.xianguo" android:name="android.test.InstrumentationTestRunner" />
<strong>android:targetPackage</strong>指明要运行的测试用例的包名。
<h3>2、继承AndroidTestCase，编写测试用例。</h3>
其实AndroidTestCase是继承自junit.framework.TestCase，因此就可以用JUnit的语法和规则来编写测试用例了。

编写完成之后，鼠标右键，[Run As]----[Android Junit Test] 单个运行测试用例。
<h3>3、使用TestSuite统一运行</h3>
编写AllTests.java：
	import junit.framework.Test;
	import junit.framework.TestSuite;
	import android.test.suitebuilder.TestSuiteBuilder;
	public class AllTests extends TestSuite {
		public static Test suite() {
			return new TestSuiteBuilder(AllTests.class).includeAllPackagesUnderHere().build();
		}
	}
执行此类，就会统一自动执行同一个包下的所有测试用例了。

