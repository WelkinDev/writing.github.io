---
title: Mac下ESP依赖环境安装
date: 2022-10-17 16:56:51
tags:
    - ESP
categories: 
    - ESP
    - 译文
---

# Mac下ESP依赖环境安装
ESP-IDF 将使用 macOS 上默认安装的 Python 版本。
* 安装 CMake 和 Ninja 编译工具：
    * 若有 [HomeBrew](https://brew.sh/)，可以运行:
    `brew install cmake ninja dfu-util`
    * 若有 [MacPorts](https://www.macports.org/install.php)，可以运行:
    `sudo port install cmake ninja dfu-util`
    * 若以上均不适用，请访问 [CMake](https://cmake.org/) 和 [Ninja](https://ninja-build.org/) 主页，查询有关 macOS 平台的下载安装问题。

**Note：**
如在上述任何步骤中遇到以下错误:
```
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
```
则必须安装 XCode 命令行工具，可运行 `xcode-select --install` 命令进行安装。

## Apple M1 用户
如果使用的是 Apple M1 系列且看到如下错误提示:
```
WARNING: directory for tool xtensa-esp32-elf version esp-2021r2-patch3-8.4.0 is present, but tool was not found
ERROR: tool xtensa-esp32-elf has no installed versions. Please run 'install.sh' to install it.
```
或者:
```
zsh: bad CPU type in executable: ~/.espressif/tools/xtensa-esp32-elf/esp-2021r2-patch3-8.4.0/xtensa-esp32-elf/bin/xtensa-esp32-elf-gcc
```

需要运行如下命令来安装 Apple Rosetta 2：
```
/usr/sbin/softwareupdate --install-rosetta --agree-to-license
```

## 安装 Python 3
[Catalina 10.15 发布说明](https://developer.apple.com/documentation/macos-release-notes/macos-catalina-10_15-release-notes) 中表示不推荐使用 Python 2.7 版本，在未来的 macOS 版本中也不会默认包含 Python 2.7。执行以下命令来检查您当前使用的 Python 版本:

```
python --version
```

如果输出结果是 `Python 2.7.17`，则代表您的默认解析器是 Python 2.7。这时需要您运行以下命令检查电脑上是否已经安装过 Python 3:

```
python3 --version
```

如果运行上述命令出现错误，则代表电脑上没有安装 Python 3。
请根据以下步骤安装 Python 3：

* 使用 [HomeBrew](https://brew.sh/) 进行安装的方法如下:
```
brew install python3
```
* 使用 MacPorts 进行安装的方法如下:
```
sudo port install python38
```

