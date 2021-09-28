---
title: Java编译、反编译与混淆
date: 2021-09-28 19:52:26
tags: Java
category: 
    - Java
    - Compile
    - Decompile
    - Anti-Decompile
---

### Java编译与执行过程

在谈反编译前首先应该知道Java是如何编译和执行的，这样才能知道为什么会被反编译。

以下述代码为例
* 我们首先使用终端`touch Simple.java`创建文件，并添加以下内容

```Java
public class Simple {
     public static void main(String[] args) {
        Inner inner = new Inner();
        inner.sayHello();
    }
}
class Inner {
    public void sayHello() {
        System.out.println("Hello, Java.");
    }
}
```

* 然后编译此文件并执行查看效果

```Shell
 $ javac Simple.java
 $ java Simple
 Hello, Java.
```


#### 编译
那么，在我们执行`javac`命令时发生了什么呢？如图，执行命令后经历了如下过程，最终生成了字节码

![](https://i.loli.net/2021/09/28/NlQaT6DrqHzLAm4.jpg)

或精简为下图
![Compile](https://i.loli.net/2021/09/28/4PcJsnkepvZWKUS.png)

此时我们生成了两个.class文件
![](https://i.loli.net/2021/09/28/xvpmqs7awNfeXHr.jpg)

因为class文件包含的是字节码(byte code)，因此当我们使用`vi`命令查看时，会发现是乱码

```Shell
$ vi Simple.class
Êþº¾^@^@^@<^@^U
^@^B^@^C^G^@^D^L^@^E^@^F^A^@^Pjava/lang/Object^A^@^F<init>^A^@^C()V^G^@^H^A^@^EInner
^@^G^@^C
^@^G^@^K^L^@^L^@^F^A^@^HsayHello^G^@^N^A^@^FSimple^A^@^DCode^A^@^OLineNumberTable^A^@^Dmain^A^@^V([Ljava/lang/String;)V^A^@
SourceFile^A^@^KSimple.java^@!^@^M^@^B^@^@^@^@^@^B^@^A^@^E^@^F^@^A^@^O^@^@^@^]^@^A^@^A^@^@^@^E*·^@^A±^@^@^@^A^@^P^@^@^@^F^@^A^@^@^@^A^@ ^@^Q^@^R^@^A^@^O^@^@^@-^@^B^@^B^@^@^@^M»^@^GY·^@        L+¶^@
±^@^@^@^A^@^P^@^@^@^N^@^C^@^@^@^C^@^H^@^D^@^L^@^E^@^A^@^S^@^@^@^B^@^T
```
![](https://i.loli.net/2021/09/28/aibILGWAuyCMn4j.jpg)

#### 执行
class文件的执行可以参考如下两图
![](https://i.loli.net/2021/09/28/nIKo2vVh1QclNTW.jpg)
![](https://i.loli.net/2021/09/28/JVaZ3e2NfUbAQGE.png)

至此，我们基本了解了Java从编译到运行的全过程。从中我们可以看出，因为class文件最终是要在JVM中执行的，中间无论是经过了怎样的加密，最终执行前都要解密，所以加密只会推迟被反编的时间，但是不能完全防止。
混淆会改变类、接口、枚举的名称，以及其中的方法、属性名称，以降低可读性的方式来保护我们的源码，这种方式目前是非常普遍的。

### 反编译
常见的反编译工具有很多
比较老牌的如[JD-Core](https://github.com/java-decompiler/jd-core)，对应的GUI工具为[JD-GUI](https://github.com/java-decompiler/jd-gui)，但是这款工具已经很久不更新了

因为我现在使用的是最新的Mac系统Monterey，已经无法使用JD，所以此处使用的是[jadx](https://github.com/skylot/jadx)，可以[下载](https://github.com/skylot/jadx/releases/tag/v1.2.0)对应的系统版本

![](https://i.loli.net/2021/09/28/ATkiwnKLxSqFbWI.jpg)

如图为解压后的目录结构，`cd`至`bin`目录后，执行`./jadx-gui`即可启动
![](https://i.loli.net/2021/09/28/PcC8oaiOtU5XkK2.jpg)



