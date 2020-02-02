---
layout: post
title: Git Summary
subtitle:
date: 2019-02-20
published: True
tags:
  - git
---

# git 
## git学习和查阅
廖雪峰官网（https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000）    https://git-scm.com/docs

git cheet sheet (https://www.git-tower.com/learn/cheat-sheets/git)

# git remote
## git 改变远端 url
```
# 展示git remote origin url
git remote -v
# reset remote origin
git remote set-url origin 
https://github.com/USERNAME/REPOSITORY.git
```
## git pull 远端的某一分支

```bash
# 显示远程分支
git branch -r
# git checkout origin/{远程分支位置}
```

[Ref](https://gaohaoyang.github.io/2016/07/07/git-clone-not-master-branch/)

## 删除远端一分支  

branch_to_delete [链接](https://stackoverflow.com/questions/44657989/why-cant-i-delete-a-branch-in-a-remote-gitlab-repository)
git push origin :branch_to_delete
push 非master分支branch_to_push到远端 
git push origin branch_to_push 

## 下载下一层
git clone --depth 1 https://github.com/tensorflow/models

# git files
## 删除已经放入git的文件和文件夹
```
# 删除文件
git rm filename
# 删除文件夹
git rm -r directory
```
## 已经被忽略的文件夹中，添加其下子目录

git add -f file_name
## git untracked working file would be overwritten 
```
The following untracked working tree files would be overwritten by merge:
```
解决办法入下：删除文件（慎重！！）
```
git clean -d -fx
```
## 删除git历史中的大文件
```bash
# show top biggest 10 files
git ls-tree -r -t -l --full-name HEAD | sort -n -k 4 | tail -n 10
# remove file 
git rm -r --cached {file_name}
# commit the change 
git commit --amend - CHEAD
```
[Ref1](https://stackoverflow.com/questions/9456550/how-to-find-the-n-largest-files-in-a-git-repository)
[Ref2](https://help.github.com/en/github/managing-large-files/removing-files-from-a-repositorys-history)
## 查看文件修改历史
```
 git log --pretty=oneline filename
```

# git version control

## 版本回退
git rest --hard HEAD^




## git merge 有冲突

(链接)[https://blog.csdn.net/soulwyb/article/details/89305387]
1. git diff，  
2. 找到文件直接修改
3. git add .,  commit 
4. git merge 


## git 修改commit message
```
git commit --amend
```
