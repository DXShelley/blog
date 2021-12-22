---
title: 版本选型
tags:
  - programing
  - version
  - release
categories:
  - programming
date: 2021-12-21 17:19:23
---

# 选型

## 版本种类

```properties
#眼花缭乱
snapshot 快照  alpha 内测  beta 公测  release 稳定版本  GA(general availability) 最稳定版本
Final 正式版  Pro(professional) 专业版   Plus 加强版
Retail 零售版   DEMO 演示版   Build 内部标号   Delux 豪华版 （deluxe：豪华的，华丽的）
Corporation或Enterpraise 企业版
M1 M2 M3 M是milestone的简写 里程碑的意思
RC 版本RC:(Release Candidate)，几乎就不会加入新的功能了，而主要着重于除错
SR(Service Release) 修正版    Trial 试用版    Shareware 共享版   Full 完全版
```

## 常用版本

```properties
#常用
build-snapshot：开发版本，也叫快照版本。当前版本处于开发中，开发完成之后自己测试和让别人测试
(通常Build后面的数字越大，软件版本越新,例如：Windows 优化大师 v5.4 Build 602)  

M1...M2（Milestone）：里程碑版本，在版发布之前 会出几个里程碑的版本。使用snapshot版本开发了一个时间，觉得最近写代码杠杠的，那么就整几个里程碑版本记录下吧，记录我们这个重大的时刻，是你我未来的回忆。

RC1…RC2（Release Candidates）：发布候选。内部开发到一定阶段了，各个模块集成后，经过细心的测试整个开发团队觉得软件已经稳定没有问题了，可以对外发行了。

release：正式版本。发布候选差不多之后，那么说明整个框架到了一定的阶段了，可投入市场大面积使用了，那么发布出去，让广大用户来吃吃香吧。

SR1…SR2（Service Release）：修正版。这是啥意思呐，这不release版本发布之后，让广大群体使用了嘛，再牛逼的架构师，也无法写出零bug的代码，那么这时候，就优先对于release版本的问题进行修复，这时候每次迭代的版本就是SR1,SR2,SR3。
```

## 版本迭代

```properties
#开发流程的版本迭代
snapshot –>  M1…MX  –> RC1…RCX  –> release –> SR1…SRX

对应的文字理解：
(1)开发版本(BS) --(开发到一个小阶段，就要标记下)--> 里程碑版本(MX) 
(2)里程碑版本(MX) --(版本到了一个相对稳定的阶段可以对外发行但还存在修复的问题，此时只做修复，不做新功能的增加)--> 发布候选(RC1)
(3)发布候选(RC1)--(BUG修复完成，发布)-->正式版本(release) 
(4)正式版本(release) --(外界反馈存在一些问题，进行内部在修复)--> 修正版本(SRX)

#结论：版本格式-> 主版本号.子版本号.修正版本号.软件版本阶段
```

## 网站英文版本标识

- CURRENt: 当前推荐的版本
- GA:　稳定版，可用于生产
- PRE: 预览版本/里程碑版(M1,M2....milestone)
- SNAPSHOT: 快照(打死不选)

## 选择

1. 打死不用 非稳定版本/ end-of-life(不维护)版本
2. release版本先等等(刚发布等别人去探雷)；
3. 推荐 SR2以后的可以放心使用；

