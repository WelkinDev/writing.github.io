---
title: SSH 密钥
date: 2021-09-24 20:10:11
tags: regulation
category: 
    - Regulation
---

**1.创建 SSH 密钥**

以用RSA算法生成密钥为例，在生成前需要先检查一下之前是否已经生成过，在Mac、Linux、Windows平台ssh密码均存放在 `~/.ssh/id_rsa.pub`下，可以使用`cat`命令尝试打印

Mac、Linux：
```shell
cat ~/.ssh/id_rsa.pub
```

Windows：

```shell
clip < ~/.ssh/id_rsa.pub
```

GNU/Linux (requires xclip):
```shell
xclip -sel clip < ~/.ssh/id_rsa.pub
```

如果返回一串以 ssh-rsa 或 ssh-dsa 开头的字符串, 说明已存在本地公钥，可以跳过生成步骤。

如果`cat`命令没有输出内容，则可以使用如下命令来生成：

```shell
ssh-keygen -t rsa -C "your@email.com"
```

如下图所示调用命令后，会提示输入一个位置去存放公钥、私钥文件，可以直接回车使用默认位置。公钥文件以 .pub 扩展名结尾，可以公开给其他人，而没有 .pub 扩展名的私钥文件不要泄露。

![](https://i.loli.net/2021/09/24/U71pewlOXNdYxsy.jpg)

**说明**

您可以选择使用口令保护私钥文件。如果您不想在每次使用 SSH 协议访问仓库时，都要输入用于保护私钥文件的口令，您可以在创建公钥、私钥文件时，输入空口令。


**2.0 使用 SSH 密钥**

复制.pub中的公钥后，前往需要的地方粘贴即可。