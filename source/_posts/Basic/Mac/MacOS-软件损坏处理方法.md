---
title: MacOS 软件损坏处理方法
date: 2019-01-13 16:29:09
tags: Basic
category: 
    - Basic
---

1、macOS High Seirra 安装破解软件打开后提示“xxx”已损坏，打不开，您应该将它移至垃圾篓的解决方法：

打开终端，然后输入以下命令：sudo spctl --master-disable 然后回车，输入系统密码后按回车（这里输入密码不会显示），如果没有提示即操作成功。

打开系统偏好设置进入“安全性与隐私”，查看“允许从以下位置下载的应用”是否选中“任何来源”，如果已选中即操作成功，再打开破解软件就不会再有打不开的提示了。

2、App 在macOS Catalina下提示已损坏无法打开解决办法：
打开终端；
输入以下命令，回车；
sudo xattr -d com.apple.quarantine /Applications/xxxx.app
注意：/Applications/xxxx.app 换成你的App路径
重启App即可。