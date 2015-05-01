---
title: "Github for Windows 下载安装失败的解法"
layout: post
tags: [github, windows]
---

`Win+R`

把`rundll32 %SystemRoot%\system32\dfshim.dll CleanOnlineAppCache`复制进去

然后`Enter`

之后最好是把`C:\Users\你的用户名\AppData\Local\Apps`这个`Apps`文件夹删了

然后就可以正常安装了

在IE浏览器键入`https://github-windows.s3.amazonaws.com/GitHub.application` ->> `Enter`

> 之前可以在Internet Options里的受信任站点里把`https://github-windows.s3.amazonaws.com/GitHub.application`添加进去