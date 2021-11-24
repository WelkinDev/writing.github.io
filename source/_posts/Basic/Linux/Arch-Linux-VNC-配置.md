---
title: Arch Linux VNC 配置
date: 2021-11-04 20:17:00
tags:
    - Arch Linux
    - Manjaro
category: 
    - Arch Linux
    - Manjaro
    - VNC
---


## 环境
**硬件：** Dell Optiplex 7090
**系统：** Manjaro 21.1.5(Linux 513)
**VNC:** TigerVNC
**桌面环境：** xfce

## 步骤

### 准备阶段
- 更新包管理器环境
```bash 
sudo pacman -Syu
```

- 安装`TigerVNC`以及`xfce`

```bash
sudo pacman tigervnc xfce4
```

### 配置
1. 用 `vncpasswd` 创建密码，它会将哈希处理之后的密码存储在 `~/.vnc/passwd`。
2. 编辑 `/etc/tigervnc/vncserver.users` 来定义用户映射。该文件中定义的每个用户都会拥有对应的端口来运行会话。该文件中的数字对应的是 TCP 端口。默认情况下，:1 是 TCP 端口 5901 (5900+1)。如果需要运行一个并行的服务端，第二个实例可以运行在下一个最大的、未被占用的端口，即 5902 (5900+2)。
3. 创建 `~/.vnc/config`，其中至少要有一行定义会话的类型，比如 `session=xfce` （可以将xfce替换为你想要运行的桌面环境）。你可以通过查看 `/usr/share/xsessions/` 里的 `.desktop` 文件来知道有哪些桌面环境在当前系统上可以使用。


`/etc/tigervnc/vncserver.users`文件示例配置如下：
```
:1=YourUserName
```

`~/.vnc/config`文件示例配置如下：
```
session=xfce
geometry=1920x1080 // resolution
```

### 启动与停止
**启动**
```
sudo systemctl start vncserver@:1
```
**停止**
```
sudo systemctl stop vncserver@:1
```
**查看当前状态**
```
systemctl status vncserver@:1.service

// It will be shown below
● vncserver@:1.service - Remote desktop service (VNC)
     Loaded: loaded (/usr/lib/systemd/system/vncserver@.service; enabled; vendor preset: disabled)
     Active: active (running) since Tue 2021-10-05 04:21:35 CST; 2h 58min ago
    Process: 520 ExecStart=/usr/bin/vncsession-start :1 (code=exited, status=0/SUCCESS)
   Main PID: 532 (vncsession)
      Tasks: 1 (limit: 18853)
     Memory: 2.2M
        CPU: 16ms
     CGroup: /system.slice/system-vncserver.slice/vncserver@:1.service
             ‣ 532 /usr/bin/vncsession yanqing :1

10月 05 04:21:35 yanqing-optiplex7090 systemd[1]: Starting Remote desktop service (VNC)...
10月 05 04:21:35 yanqing-optiplex7090 systemd[1]: Started Remote desktop service (VNC).
```

**设置开机自启动**
```
sudo systemctl enable vncserver@:1.service
```

## Reference
[TigerVNC](https://wiki.archlinux.org/title/TigerVNC)
[Xfce](https://wiki.archlinux.org/title/Xfce)