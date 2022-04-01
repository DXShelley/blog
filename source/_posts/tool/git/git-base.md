---
title: git 基础
tags:
  - tools
  - git
  - base
categories:
  - tool
  - git
date: 2021-12-21 19:49:55
---

# git

[toc]

## 背景

- 如何避免功能之间的相互干扰

- 如果快速对线上bug进行修复并上线

- 如何保证功能提测和上线的一致性

## 目标

- 实现git普通基本操作
- 实现git分支创建、合并和冲突解决
- 能规范使用git用于版本控制和发布

## 基本概念

## 基本操作

### diff

![img](git-base/diff.svg)

### 合并冲突

警告：运行`git-merge`时含有大量的未commit文件很容易让你陷入困境，这将使你在冲突中难以回退。因此非常不鼓励在使用`git-merge`时存在未commit的文件，建议使用`git-stash`命令将这些未commit文件暂存起来，并在解决冲突以后使用`git stash pop`把这些未commit文件还原出来

### 提交历史中搜索文本-git grep

要搜索提交内容(即实际的源代码行，而不是提交消息等)

```bash
#要搜索提交内容(即实际的源代码行，而不是提交消息等)
git grep <regexp> $(git rev-list --all)
#更新：如果遇到"参数列表太长"错误，git rev-list --all | xargs git grep 将工作
git grep <regexp> $(git rev-list --all | xargs git grep)
#如果要将搜索限制在某些子树(例如"lib/util")，则需要将其传递给rev-list子命令和grep：
git grep <regexp> $(git rev-list --all -- lib/util) -- lib/util

#在Rev1和Rev2之间的所有修订中搜索与正则表达式regexp匹配的文本：
git grep <regexp> $(git rev-list <rev1>..<rev2>)
```

### 跨所有分支搜索文本-git log

```bash
# 在所有提交历史中搜索commit message包含的文本
$ git log --grep='采购方案'
# 查看文本关联提交及每个提交具体修改情况（速度很快，在每个提交中搜索每个具体文件内容）
git log -p --all -S 'search string'
git log -p --all -G 'match regular expression'

$  git log --since=2021.10.20 --until=2021.10.25 -S 'reportPurchasingMethod' -- sql/

#在所有提交历史中搜索文本所在的提交
git rev-list --all | xargs git grep <regexp>
#然后可以使用git show获取更多信息，如作者、日期、差异
git show 6988bec26b1503d45eb0b2e8a4364afb87dde7af
```



## 分支管理

### Git Flow

![img](git-base/git-model@2x-16342164982891.png)

- 所有在master分支上的Commit应该对应到具体的Tag

- release分支基于develop分支创建 (记住：一旦打了release分支之后不要从develop分支上合并新的改动到release分支)

- hotfix分支基于master分支创建，开发完后测试后，需要合并回master分支和develop分支，同时在master上打一个tag

  

## 配置



## 参考

[Learn Git Branching可视化](https://learngitbranching.js.org/?locale=zh_CN)

