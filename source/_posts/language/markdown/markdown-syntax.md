---
title: markdown语法示例
tags:
  - syntax
  - markdown
  - example
categories:
  - language
  - markdown
date: 2021-12-21 18:56:26
---

[toc]

# 块元素

## 列表

### 无序列表

+ 这是无序列表
+ * 嵌套列表
  * * 嵌套列表
    * * 还是嵌套列表

### 有序列表

1. 这是有序列表
2. 1. 嵌套有序列表
   2. 1. 又是嵌套

### 任务列表

- [x] 任务一
- [x] 任务二
- [ ] 任务三

## 代码块

```java
public class hello {
    public static void main(String [] args) {
        System.out.println("helloworld");
    }
}
```

## 表格

| 字段1 | 字段2 | 字段3 |
| :---- | :---: | ----: |
| 1     |   2   |     3 |
| 4     |   5   |     6 |
| 7     |   8   |     9 |



## 引用

> 这是引用
>
> 这是引用
>
> > 还是引用

## 脚注

这是一段文字，文字中添加了[^脚注1].

## 这是水平线

---

# 行内元素

## 链接

### 外部链接

#### 行内链接

这是[行内链接](http://www.baidu.com)的例子1

这是<http://www.baidu.com>的例子2

#### 参考链接

这是[参考链接][参考链接]的例子

### 内部链接

这是[内部链接](# 块元素)的例子

## 插入图片

这是一个图片。使用链接插入。![章鱼哥](markdown-syntax/th.jpg "章鱼哥")

再来一个图片![章鱼哥2](markdown-syntax/fish.jpg "章鱼哥2号")

## 行内代码

java的输出打印是 `System.out.println("hello markdown")`.

## 字体样式

### 强调

*强调1*

_强调2_

### 加粗

**加粗了**

__加粗了又__

### 删除线

~~删除了，不要了~~

### 高亮显示

==高亮显示哦==

### 小图标（Emoji ）

这个是开心的小图标:happy:

这是愤怒的小图标::angry:



# HTML

待完善

# 参考链接

[参考链接]:http://www.jianshu.com	"简书地址"

# 脚注

[^脚注1]: 这是脚注1 的内容

