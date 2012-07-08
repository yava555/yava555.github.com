---
layout: post
title: 在Eclipse中配置SWT
wordpress_id: 36
wordpress_url: http://www.hijava.org/?p=36
date: 2008-09-10 16:20:50.000000000 +08:00
---
只需要在项目属性Add External JARs处添加 org.eclipse.swt.win32.win32.x86_3.4.0.v3448f.jar，随着eclipse版本的变化SWT JAR包的名称可能也会有相应变化，现在使用的eclipse版本是3.4.0
	import org.eclipse.swt.widgets.*;

	public class Test {

		public static void main(String[] args) {
			Display display = new Display();
			Shell shell = new Shell(display);
			shell.setText("www.hijava.org");
			shell.setSize(500, 400);
			shell.open();
			while (!shell.isDisposed()) {
				if (!display.readAndDispatch())
					display.sleep();
			}
			display.dispose();
		}

	}
