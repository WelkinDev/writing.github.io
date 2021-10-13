---
title: 'TinyB: org.bluez.Error.NotReady问题修复'
date: 2021-10-13 19:43:21
tags: 
    - Linux
    - BugFix
category: 
    - Linux
    - Bluetooth
---

## 环境
**硬件：** 树莓派4B
**系统：** Arch Linux

在上述环境下，使用TinyB（依赖Bluez）进行蓝牙相关功能的调用，报错如下

```Shell
tinyb.BluetoothException: GDBus.Error:org.bluez.Error.NotReady: Resource Not Ready
```

## 问题原因
此问题可能有两种原因：
1. Bluetooth软件被禁用
2. 蓝牙服务虽已启动，但是开关未打开（power off状态）


修复方式包括：
1. 立即打开蓝牙开关
2. 设置蓝牙服务启动后，自动打开开关

## 修复
### 1. Blocked
使用`rfkill list`命令查看当前无线设备状态

```Shell
$ rfkill list
0: hci0: Bluetooth
        Soft blocked: yes
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```
若蓝牙为block状态，可以使用`rfkill unblock all`调整为unblock状态，若状态是非block状态，可以继续尝试下述操作

### 2. Power
#### 2.1 调整power状态
调用`bluetoothctl power on`命令启动，或者可以先使用`bluetoothctl`命令进入蓝牙控制台，然后再使用`power on`命令打开开关
![](https://i.loli.net/2021/10/13/CqYVD6i1lMzy8Sm.jpg)

此时蓝牙功能已均可正常使用了。

#### 2.2 设置自启动
编辑`/etc/bluetooth/bluetooth.conf`文件中的`AutoEnable=false`部分，调整为`true`

```Shell
vim /etc/bluetooth/bluetooth.conf
```

此时在设备重启后，蓝牙服务会自动启动并处理打开状态。


## Reference 
[bluetooth.service running, but bluetoothctl says "org.bluez.Error.NotReady"](https://unix.stackexchange.com/questions/508221/bluetooth-service-running-but-bluetoothctl-says-org-bluez-error-notready)