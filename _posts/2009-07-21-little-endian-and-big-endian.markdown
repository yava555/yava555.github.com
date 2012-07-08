---
layout: post
title: little endian和big endian
wordpress_id: 450
wordpress_url: http://www.hijava.org/?p=450
date: 2009-07-21 09:32:10.000000000 +08:00
---
little endian和big endian是表示计算机字节顺序的两种格式,所谓的字节顺序指的是长度跨越多个字节的数据的存放形式.
假设从地址0x00000000开始的一个字中保存有数据0x1234abcd,那么在两种不同的内存顺序的机器上从字节的角度去看的话分别表示为:
1)little endian:在内存中的存放顺序是0x00000000-0xcd,0x00000001-0xab,0x00000002-0x34,0x00000003-0x12
2)big  endian:在内存中的存放顺序是0x00000000-0x12,0x00000001-0x34,0x00000002-0xab,0x00000003-0xcd

需要特别说明的是,以上假设机器是每个内存单元以8位即一个字节为单位的.
简单的说,ittle endian把低字节存放在内存的低位；而big endian将低字节存放在内存的高位.
现在主流的CPU,intel系列的是采用的little endian的格式存放数据,而motorola系列的CPU采用的是big endian.

转自：<a href="http://www.chinaunix.net/jh/23/823662.html" target="_blank">http://www.chinaunix.net/jh/23/823662.html</a>
