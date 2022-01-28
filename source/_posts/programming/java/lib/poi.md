---
title: poi基本使用
tags:
  - programming
  - java
  - lib
  - poi
categories:
  - programming
  - java
  - lib
date: 2022-01-20 14:50:00
---

# POI

## 基本使用

### 设置列宽

#### 列实际显示字符个数

setColumnWidth(int columnIndex, int width)设置的宽度包括4像素的边距填充（每侧两个），加上网格线的1像素填充。

如果字符宽度为w像素, w单位为一个字符宽度的1/256，设置列宽字符个数为count，则实际可见字符数X：
    X * (w * 256) + 5 = count * (w * 256) 
转换公式：
    X = count - 5/w
可见实际可见字符数比设置字符数略小。

将某个excel中的某一列列宽设置为35（该数值是Excel中显示的列宽值）

```java
sheet.setColumnWidth(0,35 * 256 + 184);
```

