---
title: 修复Ubuntu多用户情况下的VNC花屏问题
date: 2021-10-18 19:16:48
tags:
    - Linux
    - BugFix
category: 
    - Linux
    - VNC
---

## 环境
* Ubuntu 21.04
* VNC4Server
* 桌面环境：xfce4

## 花屏修复
![](https://i.loli.net/2021/10/18/g6oibR1lUY79P4k.jpg)

**调整`xstartup`文件**
* 若是root环境，文件位于`/root/.vnc/xstartup`
* 若是其他用户环境，文件位于`~/.vnc/xstartup`

以普通用户为例(使用xfce4桌面)：

```Shell 
$vim ~/.vnc/xstartup

# 原始内容为:

#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

# 方案1-修改为以下内容:

unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
startxfce4 &

# 方案2-修改为以下内容:
xrdb $HOME/.Xresources
startxfce4 &
```

调整完成后，使用下述命令给文件提权

```Shell
sudo chmod +x ~\.vnc\xstartup
```

**重启系统或重启VNCServer**

```Shell
ps -ef | grep vnc
```
上述命令可以列举出所有VNC服务，然后使用`vncserver -kill :YourVNCServerNumber`即可关闭对应的vnc服务

**Note：**
`vncserver -kill :number`命令，仅可关闭当前用户的vnc服务

最后，使用`vncserver`命令重新启动一个vnc服务即可
![](https://i.loli.net/2021/10/18/yUJYZh3ap85MjkT.jpg)



## Reference

[vnc4server](http://manpages.ubuntu.com/manpages/bionic/en/man1/vnc4server.1.html#name)
[VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

[How to Install and Configure VNC on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04)

[Ubuntu安装vnc并解决花屏问题](https://www.google.com.hk/search?q=Ubuntu+VNC花屏+多用户)

[Virtual Network Computing](https://en.wikipedia.org/wiki/Virtual_Network_Computing)