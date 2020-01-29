---
layout: post
title: "Ubuntu 18.04 shawdowsocks配置; clash配置"
subtitle: 整体概念和疑问
date: 2018-09-01
published: False
tags:
  - 工具
---



# 前言
之前用学校的vpn科学上网，然而我科技大国技术太高强，跪了。于是打算ubuntu机器上装shadowsocks。实话说搞了很久，google，baidu。

有个疑惑吧（当然也有可能是我不太会搜集信息）：翻阅了不少博客，很少发现有整体性的介绍。比如说直接说你需要设置几个模块这种，没有整体印象，大多陷入细节。然而由于系统和版本的原因，很多细节又不能重现。

# shadowsocks 配置

## 主要步骤
首先是整体印象，我总结的安装配置的四个步骤是：
1. 安装shadowsocks
1. 配置shadowsocks参数
1. 配置电脑网络设置
1. 配置开机自启动（还未完成）

下面是细节介绍：

### 安装shdowsocks

尝试terminal安装未果，最后ubuntu 软件中心安装shadowsocks

### 配置shadowsocks参数

这个步骤网上到处是, 比如[使用shadowsocks科学上网](https://medium.com/@moreless/%E4%BD%BF%E7%94%A8shadowsocks%E7%A7%91%E5%AD%A6%E4%B8%8A%E7%BD%91-87ac5efecd8a)


我也遇到到一些问题：
+ 按照以上博客尝试 ```sserver -c /etc/shadowsocks/config.json -d start``` 得到错误信息　```Permission denied: '/var/run/shadowsocks.pid```。 参考[链接](https://github.com/shadowsocks/shadowsocks/issues/1041#issue-270349758),　同时使用　whereis ssserver 命令。　改用　```sudo /home/{username}/.local/bin/ssserver -c /etc/shadowsocks/config.json -d start```
+ 得到错误信息　```socket.error: [Errno 99] Cannot assign requested address```，　参考[链接](https://github.com/shadowsocks/shadowsocks/issues/298)，修改为　```sudo /home/{user_name}/.local/bin/sslocal -c /etc/shadowsocks/config.json -d start```

### 配置电脑网络设置

这个步骤好多博客都没写，导致我安装配置好shadowsocks后还是不能科学上网，纠结了好久。这才是整体印象的重要性，你都不知道有这么个步骤。

这个步骤分为两步
+ genpac 生成autoproxy.pac文件
+ 添加autoproxy.pac文件路径到ubuntu网络代理设置中


具体细节参见[Ubuntu16.04下配置shadowsocks（亲测可用）](https://blog.csdn.net/mynameis121/article/details/70191057)


### 配置开机自启动

我还未完成

我现在暂时解决方案:写了个start.sh, 每次开始在terminal开启。



## 主要逻辑：
说下一些主要逻辑吧：

+ /etc/shadowsocks/config.json 存放配置文件
+ /var/log/shadowsocks.log 存放log文件


## 疑问
还有些疑问没解决

+ ssserver, sslocal 命令有啥区别？
+ 开机自启动还没完成啊

## 总结

+ 总感觉在干一件事情的时候，必须需要有个整体的概念才行。感觉这样才不至于陷于细节不能自拔
+ 虽说是个工具，然而工具不好用，还是很尴尬的，验证影响心情和效率。




# Linux clash 配置
## 配置步骤:
1. clash 配置
  2. 下载clash并解压二进制文件(目前双击文件没有反馈,然而完成启动)
  3. 运行一次clash后, 自动产生文件夹/home/userid/.config/clash; 更新config.yaml文件;
  4. clash.razord.top 可查看clash配置
2. linux 电脑配置
  3. 打开网络->系统代理->手动, 根据config.yaml 修改http, socks代理ip和端口
  4. 重启clash后可用


## 目前使用方法:
1. 每次开机后必需手动打开clash文件,如果不打开则国内网络也连不了

## 参考文献
[Clash For Linux 安装及使用](https://www.jianshu.com/p/2906066d2e0a)
