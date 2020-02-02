---
layout: post
title: Linux Shell & Windows CMD
subtitle:
date: 2019-02-02
published: True
tags:
  - linux shell
  - window cmd
---
## 参考文献
[中文资料](http://www.runoob.com/linux/linux-shell.html)
## 性能测试
### /usr/bin/time
1. 记录程序运行时间和内存 [链接](https://gist.github.com/tkuchiki/4b77005cc64426b28c3d)
```
/usr/bin/time -v --output=../time.log  python test.py  > test.log 
```

2. 输出程序最大占用内存：

    /usr/bin/time -f "%M" --output=../time.log python test.py > test.log




## vim
### DOC, LINUX引起的格式问题
[链接](https://www.zhihu.com/question/22130727)

可以用vi打开，执行 :%s/^M//g　来去掉^M(^M是ctrl+v,ctrl+m) 

## 文本文件
### grep
#### 显示行数
```
 tail -n 10000 move.log | grep -b "content"
```

#### 

## 文件目录

### 创建文件夹
-p  如果不存在则建文件夹
```
mkdir -p 
```
### ~  /
cd ~     回到 user/
cd /     回到 /
### 查看目录下文件大小
`du -h --max-depth=1` 
### ll
ll =  ls -l   (ubuntu 中没有)


### find
1.  查找目录和子目录下文件

    find . -name 'name.py'
2. 查找所有子目录中文件并删除
```bash
find . -name "*.o"  | xargs rm -f
``` 
3. 查找目录下所有文件是否包含字符串
```
find . | xargs grep -ri '字符串'
```
-r : recursive
-i : ignore case 


### 文件下文件多少
所有文件多少

    ls -l | wc -l

文件夹数目

    ls -l | grep "^d" |wc -l

文件的数目

    ls -lR| grep "^-" | wc -l
### zip 命令

    zip -r target.zip target_directory/

### tar.gz 文件解压
[博客链接](https://blog.csdn.net/maray/article/details/4312768)
### 文件夹下文件大小

#### du命令 当前目录下大小，并排序
du -h --max-depth=1
### 脚本中source命令的运行
用source运行脚本，不能用bash[链接](https://blog.csdn.net/jiajianjunneusoft/article/details/7168405)

### nohup 
1. nohup 几条连续命令

nohup sh -c './cmd2 >result2 && ./cmd1 >result1' &[链接](https://unix.stackexchange.com/questions/67221/running-multiple-nohup-commands-in-background)

### 连续执行多条命令
    ; 即使前面错了，还可以继续执行
&& 前面出错，则停止执行

### 服务器和端口
1. 命令行连接服务器：  ssh 用户名@ip地址
    ssh root@192.168.66.100
2. 向服务器传输文件  scp -r 本地文件夹 用户名@ip地址：远程地址
3. 查看占用的端口，并关闭   netstat -anp | grep 端口号



## Windows cmd 命令
[参考链接](https://www.digitalcitizen.life/command-prompt-how-use-basic-commands)
### 改到D盘

    d:
    
## window putty 连接服务器
1. Putty 连接自动记录密码
    1.  右键PuTTY.exe发送一个快捷方式到桌面。重命名一下到底是干什么用的以免你弄混了。
    2.  右键属性。“目标”那里可以输入你的命令，比如"C:\Program Files\PuTTY\putty.exe" 用户名@服务器地址（不需要端口） -pw 密码可以确认了。
    3.  双击快捷方式可连接。