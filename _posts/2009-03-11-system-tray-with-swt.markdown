---
layout: post
title: 利用SWT创建系统托盘
wordpress_id: 226
wordpress_url: http://www.hijava.org/java/%e5%88%a9%e7%94%a8swt%e5%88%9b%e5%bb%ba%e7%b3%bb%e7%bb%9f%e6%89%98%e7%9b%98
date: 2009-03-11 09:32:17.000000000 +08:00
---
关键代码如下：
	Display display=Display.getDefault();
	Tray tray=display.getSystemTray();

	if(tray==null)
	{
		System.out.println("该系统不支持系统托盘！");
		return;
	}

	final TrayItem item=new TrayItem(tray,SWT.NONE);

	//将图片一起打包时，用此方法获取图片,this.getClass().getResourceAsStream().
	Image img=new Image(display,this.getClass().getResourceAsStream("fav.ico"));
	item.setImage(img);

	item.setToolTipText("系统托盘测试");//托盘文字提示

	//添加监听，鼠标右键退出
	item.addListener(SWT.MenuDetect, new Listener(){

		@Override
		public void handleEvent(Event event) {
			if(event.type==SWT.MenuDetect)
				item.dispose();
		}

	});

	while (!item.isDisposed()) {
		if (!display.readAndDispatch())
			display.sleep();
	}
	display.dispose();
item.addListener( SWT.Show, listner ); //系统托盘显示
item.addListener( SWT.Hide , listner );//系统托盘隐藏
item.addListener( SWT.Selection , listner );//系统托盘单击选中
item.addListener( SWT.DefaultSelection , listner );//系统托盘双击选中
item.addListener( SWT.MenuDetect , listner );//系统托盘右击事件
