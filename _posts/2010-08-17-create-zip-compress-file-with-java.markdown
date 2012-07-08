---
layout: post
title: 用Java创建ZIP压缩文件
wordpress_id: 931
wordpress_url: http://www.hijava.org/?p=931
date: 2010-08-17 12:58:49.000000000 +08:00
---

	/**
	 * 压缩文件夹
	 * @param sourceDIR 文件夹名称（包含路径）
	 * @param targetZipFile 生成zip文件名
	 * @author liuxiangwei
	 */
	public static void zipDIR(String sourceDIR, String targetZipFile) {
		try {
			FileOutputStream target = new FileOutputStream(targetZipFile);
			ZipOutputStream out = new ZipOutputStream(new BufferedOutputStream(target));
			int BUFFER_SIZE = 1024;
			byte buff[] = new byte[BUFFER_SIZE];
			File dir = new File(sourceDIR);
			if (!dir.isDirectory()) {
				throw new IllegalArgumentException(sourceDIR+" is not a directory!");
			}
			File files[] = dir.listFiles();

			for (int i = 0; i < files.length; i++) {
				FileInputStream fi = new FileInputStream(files[i]);
				BufferedInputStream origin = new BufferedInputStream(fi);
				ZipEntry entry = new ZipEntry(files[i].getName());
				out.putNextEntry(entry);
				int count;
				while ((count = origin.read(buff)) != -1) {
					out.write(buff, 0, count);
				}
				origin.close();
			}
			out.close();

		} catch (IOException e) {
			throw new MsgException("");
		}
	}

<strong>注意：</strong>建议使用<em>org.apache.tools.zip.*</em>包下相关类，否则可能会出现中文乱码问题。

参考：<a href="http://www.blogjava.net/dreamstone/archive/2007/08/09/134986.html" target="_blank">java 实现zip与unzip</a>
