---
title: 软件License生成实践
date: 2021-09-24 20:44:45
tags: practice
category: 
    - cryptology
---

很多商业软件在使用时需要填写、导入授权码或授权文件，本文主要尝试生成License，并能防止篡改。


## 加解密
**加密流程：**
动态AES密钥 + AES加密 + RSA签名

**解密流程：**
AES密钥解析 + RSA验签 + AES解密 



