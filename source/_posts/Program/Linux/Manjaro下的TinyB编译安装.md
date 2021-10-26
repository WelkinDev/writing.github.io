---
title: Manjaro下的TinyB编译安装
date: 2021-10-26 20:44:41
tags:
    - Linux
    - TinyB
category: 
    - Linux
    - Bluetooth
---

## 环境
**硬件：** Dell Optiplex 7090
**系统：** Manjaro
**方式：** 源代码编译安装

## 步骤

* Clone代码至本地
```Shell
git clone https://github.com/intel-iot-devkit/tinyb.git
```

* 编译前准备
后续的编译依赖了CMake（3.1+）、Make、GLib/GIO等，在Manjaro中可以通过安装`base-devel`包来直接完成基本开发包的安装。
```Shell
sudo pacman -Syu
sudo pacman -S base-devel
```

* TinyB编译安装
```Shell
mkdir build
cd build
cmake ..
// cmake .. -DBUILDJAVA=ON // if need java
make
make install
```



## Reference
[Tiny Bluetooth LE Library](https://github.com/intel-iot-devkit/tinyb)
[CMake error on Manjaro](https://github.com/wsdfhjxc/virtual-desktop-bar/issues/52)