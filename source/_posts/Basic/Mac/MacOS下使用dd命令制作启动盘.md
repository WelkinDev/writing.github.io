---
title: MacOS下使用dd命令制作启动盘
date: 2021-10-13 11:57:39
tags: Basic
category: 
    - Tools
---


## 环境
**系统：** MacOS Monterey
**版本：** 12.0 Beta版(21A5284e)

## 命令
1. diskutil
2. dd
3. brew 
4. pv
5. ls

## 步骤
* 使用`diskutil list`列出当前所有存储设备
![](https://i.loli.net/2021/10/13/oS2qzWQfHlbt9JF.jpg)

* 使用`diskutil umountDisk disk2`卸载你的U盘，此处我的是`disk2`，执行成功后会有如下输出

```Shell
Unmount of all volumes on disk2 was successful
```

* 使用`sudo dd if=input/file/path/system.iso of=/dev/disk2 bs=4m`命令写入，此命令不会显示进度，等待完成即可。

若想要显示制作进度，可以看后续步骤。

### 进度显示 

若使用的是GNU Coreutils 8.24+版本，可以添加参数`status=progress`用于显示进度。

```Shell
sudo dd if=input/file/path/system.iso of=/dev/disk2 bs=4m status=progress
```

若使用的是较低版本，可以使用`pv`命令显示

1. 使用`brew install pv`命令安装`pv`
2. 使用添加`pv`后的`dd`命令

```Shell
sudo dd if=input/file/path/system.iso | pv -s 887435264 | sudo dd of=/dev/disk2 bs=4m
```

![](https://i.loli.net/2021/10/13/nKzqghTRWfrAsLY.jpg)

其中`pv -s 887435264`中的数字为iso包的大小，可以在iso所在目录中使用`ls -la`命令查看文件的大小

![](https://i.loli.net/2021/10/13/8pCiQRJeusxz2mY.jpg)

```
1733272+0 records out
887435264 bytes transferred in 1806.902111 secs (491136 bytes/sec)
 846MiB 0:30:07 [ 479KiB/s] [============================================================================================================================================================================================================================================================================================================================>] 100%
0+13542 records in
0+13542 records out
887435264 bytes transferred in 1807.057824 secs (491094 bytes/sec)
```
完成后会有类似如上输出，现在使用启动盘了。