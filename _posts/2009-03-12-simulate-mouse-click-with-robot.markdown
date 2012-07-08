---
layout: post
title: 用robot类模拟鼠标点击
wordpress_id: 230
wordpress_url: http://www.hijava.org/?p=230
date: 2009-03-12 11:23:51.000000000 +08:00
---
	try {
		Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
		Robot robot = new Robot();
		robot.mouseMove(screenSize.width - 10, 10);
		robot.delay(2000);
		robot.mousePress(InputEvent.BUTTON1_MASK);
		robot.delay(2000);
		robot.mouseRelease(InputEvent.BUTTON1_MASK);

	} catch (AWTException e) {
		e.printStackTrace();
	}
比较有意思的一段代码。
