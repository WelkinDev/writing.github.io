---
title: Manjaro安装VSCode
date: 2021-11-23 10:54:04
tags: 
    - Manjaro
category: 
    - Manjaro
---

## Method 1：使用pacman安装

1. 搜索VSCode安装包

```Shell
sudo pacman -Ss vscode
```

```Shell
community/code 1.62.0-1
    The Open Source build of Visual Studio Code (vscode) editor
community/vscode-css-languageserver 1.62.0-1
    VS Code CSS language server
community/vscode-html-languageserver 1.62.0-1
    VS Code HTML language server
community/vscode-json-languageserver 1.62.0-1
    VS Code JSON language server
```

可以看到，在Manjaro中VSCode的名称为Code

2. 使用pacman安装

```Shell
sudo pacman -S code
```

```Shell
resolving dependencies...
looking for conflicting packages...

Packages (5) electron13-13.6.1-1  minizip-1:1.2.11-4  re2-1:20211101-1  ripgrep-13.0.0-2  code-1.62.0-1

Total Download Size:    68.05 MiB
Total Installed Size:  267.68 MiB

:: Proceed with installation? [Y/n]
:: Retrieving packages...
 electron13-13.6.1-1-x86_64                                                                                                                                                    51.8 MiB  1364 KiB/s 00:39 [##############################################################################################################################] 100%
 code-1.62.0-1-x86_64                                                                                                                                                          14.8 MiB  2.61 MiB/s 00:06 [##############################################################################################################################] 100%
 ripgrep-13.0.0-2-x86_64                                                                                                                                                     1316.7 KiB   441 KiB/s 00:03 [##############################################################################################################################] 100%
 re2-1:20211101-1-x86_64                                                                                                                                                      174.1 KiB  87.8 KiB/s 00:02 [##############################################################################################################################] 100%
 minizip-1:1.2.11-4-x86_64                                                                                                                                                     26.2 KiB  19.6 KiB/s 00:01 [##############################################################################################################################] 100%
 Total (5/5)                                                                                                                                                                   68.0 MiB  1247 KiB/s 00:56 [##############################################################################################################################] 100%
(5/5) checking keys in keyring                                                                                                                                                                            [##############################################################################################################################] 100%
(5/5) checking package integrity                                                                                                                                                                          [##############################################################################################################################] 100%
(5/5) loading package files                                                                                                                                                                               [##############################################################################################################################] 100%
(5/5) checking for file conflicts                                                                                                                                                                         [##############################################################################################################################] 100%
(5/5) checking available disk space                                                                                                                                                                       [##############################################################################################################################] 100%
:: Processing package changes...
(1/5) installing minizip                                                                                                                                                                                  [##############################################################################################################################] 100%
(2/5) installing re2                                                                                                                                                                                      [##############################################################################################################################] 100%
(3/5) installing electron13                                                                                                                                                                               [##############################################################################################################################] 100%
Optional dependencies for electron13
    kde-cli-tools: file deletion support (kioclient5)
    libappindicator-gtk3: StatusNotifierItem support [installed]
    pipewire: WebRTC desktop sharing under Wayland [installed]
    trash-cli: file deletion support (trash-put)
    xdg-utils: open URLs with desktop's default (xdg-email, xdg-open) [installed]
(4/5) installing ripgrep                                                                                                                                                                                  [##############################################################################################################################] 100%
(5/5) installing code                                                                                                                                                                                     [##############################################################################################################################] 100%
Optional dependencies for code
    bash-completion: Bash completions [installed]
    zsh-completions: ZSH completitons
    x11-ssh-askpass: SSH authentication
ldconfig: /usr/lib/libjavatinyb.so.0 is not a symbolic link

ldconfig: /usr/lib/libtinyb.so.0 is not a symbolic link

:: Running post-transaction hooks...
(1/2) Arming ConditionNeedsUpdate...
(2/2) Updating the desktop file MIME type cache...
```

## Method 2: 使用Snap安装
1. 安装并启用snapd

安装Snapd
```Shell
sudo pacman -S snapd
```

启用Snapd
```Shell
sudo systemctl enable --now snapd.socket
sudo ln -s /var/lib/snapd/snap /snap
```

2. 通过Snap安装VSCode

```Shell
sudo snap install code --classic
```

## Reference
[Installing Visual Studio Code (VSCode) on Manjaro linux](https://umaranis.com/2018/07/05/installing-visual-studio-code-vscode-on-manjaro-linux/)
[Enable snaps on Manjaro Linux and install code](https://snapcraft.io/install/code/manjaro)
[Snap Store](https://snapcraft.io/store)

