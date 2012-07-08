---
layout: post
title: SWT窗体关闭时显示确认对话框
wordpress_id: 271
wordpress_url: http://www.hijava.org/?p=271
date: 2009-03-23 16:44:19.000000000 +08:00
---
关闭窗体shell 时显示确认对话框：
	shell.addShellListener(new ShellAdapter() {
		public void shellClosed(ShellEvent e) {
		    MessageBox mb = new MessageBox(shell, SWT.ICON_QUESTION | SWT.OK | SWT.CANCEL);
		    mb.setText("Confirm Exit");
		    mb.setMessage("Are you sure you want to exit?");
		    int rc = mb.open();
		    e.doit = (rc == SWT.OK);
		}
	});
