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

先要知道Java编译、执行流程，才能找到切入点反编译，知道从哪些点儿进行反编译，才能找到准确的点进行防护。
按照这个思路，先看编译执行过程。

### Java编译与执行过程
* 创建java文件并添加测试代码

```Shell
$ touch Simple.java
$ vi Simple.java 
```

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


#### 编译: What happens at compile time in java
执行`javac`命令时发生了什么呢？如图

![](https://i.loli.net/2021/09/28/NlQaT6DrqHzLAm4.jpg)

或精简为下图
![Compile](https://i.loli.net/2021/09/28/4PcJsnkepvZWKUS.png)

本质上是将.java编译成为了字节码(byte code).class文件

此时我们使用`vi`命令查看时，看到的是如下乱码

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

#### 执行: What happens at runtime in java
class文件的执行流程可以参考如下两图
![](https://i.loli.net/2021/09/28/nIKo2vVh1QclNTW.jpg)
![](https://i.loli.net/2021/09/28/JVaZ3e2NfUbAQGE.png)

至此，我们基本了解了Java从编译到运行的全过程。从中我们可以看出，因为class文件最终是要在JVM中执行的，中间无论是经过了怎样的加密，最终执行前都要解密，所以加密只会推迟被反编的时间，但是不能完全防止。
混淆会改变类、接口、枚举的名称，以及其中的方法、属性名称，以降低可读性的方式来保护我们的源码，这种方式目前是非常普遍的。

### 反编译
常见的反编译工具有很多
比较老牌的如[JD-Core](https://github.com/java-decompiler/jd-core)，对应的GUI工具为[JD-GUI](https://github.com/java-decompiler/jd-gui)，但是这款工具已经很久不更新了

在MacOS Monterey上已经无法使用JD，所以此处使用的是[jadx](https://github.com/skylot/jadx)，可以[下载](https://github.com/skylot/jadx/releases/tag/v1.2.0)对应的系统版本

![](https://i.loli.net/2021/09/28/ATkiwnKLxSqFbWI.jpg)

如图为解压后的目录结构，`cd`至`bin`目录后，执行`./jadx-gui`即可启动
![](https://i.loli.net/2021/09/28/PcC8oaiOtU5XkK2.jpg)

选中`Sample.class`和`Inner.class`后，OpenFile即可
![](https://i.loli.net/2021/09/29/VjSP5zFbWoMhEOY.jpg)

如此，反编译完成

### Jar包
#### What is JAR?
JAR(**J**ava **AR**chive)本质上是一个ZIP文档，其中包含了class文件，也可以包含资源文件。

#### 创建JAR包
新建`manifest.txt`文件，并添加如下内容

```JSON
Manifest-Version: 1.0
Main-Class: Simple
```

使用`jar cmf Simple.jar manifest.txt *.class`命令将上述步骤中的两个class文件生成`Simple.jar`文件
添加`manifest`是为了让jar包可执行（manifest指明了jar包执行入口）

```Shell
已添加清单
正在添加: Inner.class(输入 = 396) (输出 = 285)(压缩了 28%)
正在添加: Simple.class(输入 = 314) (输出 = 242)(压缩了 22%)
```
此时生成的jar包可以使用同样的方法进行反编译。

使用`java -jar Simple.jar`可以执行jar包，效果与`Simple.class`相同

### 混淆 Obfuscation
此处使用[ProGuard](https://github.com/Guardsquare/proguard#-quick-start)进行jar包混淆，可以从[sourceforge下载](https://sourceforge.net/projects/proguard/)或者Github下载相应的包。

![](https://i.loli.net/2021/09/29/h94WVcByqdETJFS.jpg)

切换至`lib`目录后，新建配置文件`touch myconfig.pro`

```
-injar /Users/liyanqing/Documents/Test/JavaTest/Simple.jar
-outjars /Users/liyanqing/Documents/Test/JavaTest/out/Simple.jar

-dontshrink
-dontoptimize
-dontpreverify
-ignorewarnings 
-verbose

-keep public class None
```

在混淆后，再反编译出的内容就会变的可读性极差。
![](https://i.loli.net/2021/09/29/7HOyo6qgVxZGnM4.jpg)



### Reference

**Compile**
[Java 代码编译和执行的整个过程](https://wiki.jikexueyuan.com/project/java-vm/java-debug.html)

**Anti-Decompile**
[有哪些防止反编译 Java 类库 jar 文件的办法？](https://www.zhihu.com/question/19766494)
[Protect Your Java Code From Reverse Engineering](https://dzone.com/articles/protect-your-java-code-from-re)

**jar**
[JAR File Overview](https://docs.oracle.com/javase/8/docs/technotes/guides/jar/jarGuide.html)
[JAR (file format)](https://en.wikipedia.org/wiki/JAR_(file_format))

[Creating a JAR File](https://docs.oracle.com/javase/tutorial/deployment/jar/build.html)

[Modifying a Manifest File](https://docs.oracle.com/javase/tutorial/deployment/jar/modman.html)
[Create JAR with manifest](https://stackoverflow.com/questions/10125639/how-to-create-a-jar-file-using-the-terminal)

**ProGuard**
[ProGuard使用手册](https://www.guardsquare.com/manual/configuration/examples)