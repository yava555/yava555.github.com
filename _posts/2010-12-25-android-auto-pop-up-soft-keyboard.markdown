---
layout: post
title: Android自动弹出软键盘
wordpress_id: 1056
wordpress_url: http://www.hijava.org/?p=1056
date: 2010-12-25 18:30:03.000000000 +08:00
---
在AndroidManifest.xml文件，对应Activity处增加：<em>android:windowSoftInputMode="stateVisible|adjustResize"</em>

<a href="/uploads/2010/12/softinput.jpg"><img class="alignnone size-full wp-image-1057" title="softinput" src="/uploads/2010/12/softinput.jpg" alt="" width="328" height="486" /></a>

stateVisible：打开Activity时自动弹出软键盘
adjustResize：Acitivity根据屏幕中的软键盘而调整大小，可以让软键盘始终显示在屏幕下方，并且不会将操作按钮覆盖住。

参照：<a href="http://developer.android.com/guide/topics/manifest/activity-element.html#wsoft" target="_blank">http://developer.android.com/guide/topics/manifest/activity-element.html#wsoft</a>
