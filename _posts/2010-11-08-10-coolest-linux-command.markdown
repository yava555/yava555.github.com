---
layout: post
title: ! '[转]10 个最酷的 Linux 单行命令'
wordpress_id: 949
wordpress_url: http://www.hijava.org/?p=949
date: 2010-11-08 09:04:33.000000000 +08:00
---
下面是来自 <a href="http://commandlinefu.com/"><span style="color: #bb5500;">Commandlinefu</span></a> 网站由用户投票决出的 10 个最酷的 Linux 单行命令，希望对你有用。
<ol>
	<li><code><span style="color: #ff0033;">sudo !!</span></code>

以 root 帐户执行上一条命令。</li>
	<li><code><span style="color: #ff0033;">python -m SimpleHTTPServer</span></code>

利用 Python 搭建一个简单的 Web 服务器，可通过 http://$HOSTNAME:8000 访问。</li>
	<li><code><span style="color: #ff0033;">:w !sudo tee %</span></code>

在 Vim 中无需权限保存编辑的文件。</li>
	<li><code><span style="color: #ff0033;">cd -</span></code>

更改到上一次访问的目录。</li>
	<li><code><span style="color: #ff0033;">^foo^bar</span></code>

将上一条命令中的 foo 替换为 bar，并执行。</li>
	<li><code><span style="color: #ff0033;">cp filename{,.bak}</span></code>

快速备份或复制文件。</li>
	<li><code><span style="color: #ff0033;">mtr google.com</span></code>

traceroute + ping。</li>
	<li><code><span style="color: #ff0033;">!whatever:p</span></code>

搜索命令历史，但不执行。</li>
	<li><code><span style="color: #ff0033;">$ssh-copy-id user@host</span></code>

将 ssh keys 复制到 user@host 以启用无密码 SSH 登录。</li>
	<li><code><span style="color: #ff0033;">ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq /tmp/out.mpg</span></code>

把 Linux 桌面录制为视频。</li>
</ol>
转自：<a href="http://www.javaeye.com/topic/794804" target="_blank">http://www.javaeye.com/topic/794804</a>
