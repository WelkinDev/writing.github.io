---
title: Wox - Windows上的效率工具
date: 2019-01-03 16:32:29
tags: Wox
category: 
    - Tools
    - Windows
---

## Wox

 Wox - Windows上的效率工具
![timg-2](https://i.loli.net/2021/07/21/5yG4FcaAk9PViLY.jpg)


<!--李艳清
2019-01-03-->

<div STYLE="page-break-after: always;"></div>

#### 目录：

[TOC]

<div STYLE="page-break-after: always;"></div>


#### 文档信息

| 时间 | 版本 | 作者 | 备注 |
| --- | --- | --- | --- |
| 2019-01-03 | 1.0 | Welkin | Welkin.lee@hotmail.com |

<div STYLE="page-break-after: always;"></div>


#### 简介
Wox 是一款在Windows上使用的快捷启动器，它可以启动程序、执行命令行、搜索网页，还可以自定义各种功能。
[Wox官网地址](http://www.wox.one)

##### Wox可以做什么
![](https://i.loli.net/2021/07/21/EyPos3AjR5pFUve.png)


#### 基础功能篇

安装好Wox之后，Alt + Space即可打开（可在 Settings - HotKey 中进行自定义设置打开快捷键）。

##### 快捷调用

###### 执行Shell命令
输入英文状态下">"，空格后接命令即可
![](https://i.loli.net/2021/07/21/CLgD92hzbU6YSu8.jpg)

###### 快捷计算
![](https://i.loli.net/2021/07/21/kOGepL1WZ9qoFjb.jpg)


###### 快捷显示颜色
输入以#开头的Hex颜色，即可快速查看颜色效果。
![](https://i.loli.net/2021/07/21/ZDNTjVM7EPmYGgt.jpg)



##### 系统命令
###### 关闭电脑
输入命令“shutdown”
![](https://i.loli.net/2021/07/21/N2EXBwHSR3VAyql.jpg)

###### 重启电脑
输入命令“restart”
![](https://i.loli.net/2021/07/21/Fn7iRTo1JGh8wA4.jpg)

###### 锁定
输入命令“lock”
![](https://i.loli.net/2021/07/21/vfyrgPAWEu6hBzs.jpg)

###### 休眠
输入命令“sleep”
![](https://i.loli.net/2021/07/21/lEYQc5BxN1vyqdU.jpg)


##### 打开相关
快捷打开本地软件、文件等。

###### 打开链接
打开Wox后输入链接，回车后会用默认浏览器打开当前链接。
![](https://i.loli.net/2021/07/21/LGVj6qJYfa7eFA8.jpg)


###### 打开软件
输入要打开的软件名（中文或软件英文包名均可），如“微信”或“WeChat”。
![](https://i.loli.net/2021/07/21/JMuynzDf4v9mCBH.jpg)

###### 打开文件
输入想要打开的文件名，即可自动搜索所有。
![](https://i.loli.net/2021/07/21/jI5NQMPgV2GuiD1.jpg)


##### 搜索相关
搜索本地文件可直接输入文件名、文件夹名。网络搜索按在什么网站进行搜索具体添加触发关键词。

###### 搜索本地文件
![](https://i.loli.net/2021/07/21/rwKgXknPd5zYaL4.jpg)


###### 网络搜索
网络搜索的格式是：触发词 搜索内容

###### 默认触发关键词
| 触发关键词 | 描述 |
| --- | --- |
| bd  | 在百度搜索之后内容 |
| bing | 在必应搜索之后内容 |

例如：
![](https://i.loli.net/2021/07/21/SxbqgUoNnQk2X74.jpg)


![](https://i.loli.net/2021/07/21/QKMpsL5win9P8Ar.jpg)


输入完成后，回车即可自动打开默认浏览器，使用输入触发词网站进行相应搜索。

###### 其它关键词添加
Wox已经默认配置了很多，但是大多为Google相关国内并不能使用。这里补充几个国内常用的，添加方式为“Settings - 插件 - 网页搜索 - 添加”，如下图所示。
![](https://i.loli.net/2021/07/21/yvg93dXqkHT8xjb.jpg)


![](https://i.loli.net/2021/07/21/Bf3kjrEJDws5GeA.jpg)



你可以输入自己喜欢的标题、触发字、图标等，上图是以京东为例进行的填写，下面表格提供相应URL


| 搜索站点 | URL |
| --- | --- |
| 简书 | http://www.jianshu.com/search?q={q}&page=1&type=notes |
| 京东 | http://search.jd.com/Search?keyword={q}&enc=utf-8&pvid=klithfni.741mvl |
| 淘宝 | http://s.taobao.com/search?q={q} |
| 豆瓣 | https://movie.douban.com/subject_search?search_text={q}&cat=1002 |

#### 进阶功能

##### 插件
###### 插件安装
[官网插件列表地址](http://www.wox.one/plugin)
安装命令格式：wpm install 插件名称
以安装Weather.Open为例，输入插件安装命令wpm install Weather.Open，安装完成后重启Wox即可使用。

Weather.Open默认的触发关键词是forecast，可以在Settings - 插件 - Weather.Open中进行设置。
![](https://i.loli.net/2021/07/21/d19PxterNVJkTL7.jpg)


###### 插件卸载
命令格式: wpm uninstall 插件名称

###### 查看已安装插件
已安装插件命令格式： wpm list 
![](https://i.loli.net/2021/07/21/MeahGsBZj7UF5l9.jpg)


###### 禁用插件
1. 打开Wox设置界面，并切换到插件页。
2. 选择你想禁用的插件，勾选disable勾选框即可。这一操作是即时生效的。

###### 编写插件
在编写Wox插件之前，需要明白Wox使用的插件机制。

简单来说，Wox与插件之间通过标准输入输出的方式通信，使用[JSONRPC](https://www.jsonrpc.org/specification)来完成通信。使用这种方式，将极大的提高Wox支持的插件种类， 几乎任何语言都可以用来编写Wox插件。

下图展示了Wox与插件之间的通信原理：
![](https://i.loli.net/2021/07/21/zNlb5ZI9WH3Rgnm.png)


在创建Wox的时候，用户必须在插件的根目录方式一个名为plugin.json的文件。该文件中包含了该插件的一些基本信息。在用户上传插件到getwox.com的时候， Wox会读取这个文件中的信息。

plugin.json的格式如下： 请在粘贴下面代码的时候移除其中的注释

```
{
  "ID":"D2D2C23B084D411DB66FE0C79D6C2A6H",   //插件ID，32位的UUID
  "ActionKeyword":"wpm",                     //插件默认的触发关键字
  "Name":"WPM",                              //插件名字
  "Description":"Wox Package Management",    //插件介绍
  "Author":"qianlifeng",                     //作者
  "Version":"1.0.0",                         //插件版本，必须是x.x.x的格式
  "Language":"csharp",                       //插件语言，目前支持csharp,python
  "Website":"http://www.getwox.com",         //插件网站或者个人网站
  "IcoPath": "Images\\pic.png",              //插件图标，路径是相对插件根目录的路径
  "ExecuteFileName":"PluginManagement.dll"   //执行文件入口，如果是C#插件则填写DLL路径，如果是pyhton则填写python文件路径
}
```

###### Python插件编写
Wox支持使用Python进行插件的开发。Wox自带了一个打包的Python及其标准库，所以使用Python 插件的用户不必自己再安装Python环境。同时，Wox还打包了requests和beautifulsoup4两个库， 方便用户进行网络访问与解析。

参考项目：[Wox.Plugin.HackerNews](https://github.com/Wox-launcher/Wox.Plugin.HackerNews)

创建Python插件的步骤如下：
1. 创建plugin.json文件
2. 创建一个python文件，一个简单的例子如下：

```Python
#encoding=utf8
import requests
from bs4 import BeautifulSoup
import webbrowser
from wox import Wox,WoxAPI

#用户写的Python类必须继承Wox类 https://github.com/qianlifeng/Wox/blob/master/PythonHome/wox.py
#这里的Wox基类做了一些工作，简化了与Wox通信的步骤。
class Main(Wox):

  def request(self,url):
    #如果用户配置了代理，那么可以在这里设置。这里的self.proxy来自Wox封装好的对象
    if self.proxy and self.proxy.get("enabled") and self.proxy.get("server"):
      proxies = {
        "http":"http://{}:{}".format(self.proxy.get("server"),self.proxy.get("port")),
        "https":"http://{}:{}".format(self.proxy.get("server"),self.proxy.get("port"))}
      return requests.get(url,proxies = proxies)
    else:
      return requests.get(url)

  #必须有一个query方法，用户执行查询的时候会自动调用query方法
  def query(self,key):
    r = self.request('https://news.ycombinator.com/')
    bs = BeautifulSoup(r.text)
    results = []
    for i in bs.select(".comhead"):
      title = i.previous_sibling.text
      url = i.previous_sibling["href"]
      results.append({
        "Title": title ,
        "SubTitle":title,
        "IcoPath":"Images/app.ico",
        "JsonRPCAction":{
          #这里除了自已定义的方法，还可以调用Wox的API。调用格式如下：Wox.xxxx方法名
          #方法名字可以从这里查阅https://github.com/qianlifeng/Wox/blob/master/Wox.Plugin/IPublicAPI.cs 直接同名方法即可
          "method": "openUrl",
          #参数必须以数组的形式传过去
          "parameters":[url],
          #是否隐藏窗口
          "dontHideAfterAction":True
        }
      })

    return results

  def openUrl(self,url):
    webbrowser.open(url)
    WoxAPI.change_query(url)

  #以下代码是必须的
  if __name__ == "__main__":
    Main()
```


##### 主题
可以在 Settings - 主题下进行主题设置
###### 自定义主题
如果Wox自带的UI你不喜欢，可以查看[官网主题](http://www.wox.one/theme/builder)进行挑选，或者自己编写。


