---
title: excel使用技巧
tags:
  - office
  - excel
  - skill
categories:
  - office
  - excel
date: 2021-12-21 19:41:31
---

# excel

## 公式和函数

#### 最常用的10个函数

#### 日期和时间函数

##### workday

只计算工作日。excel 加天数 如果为周末顺延

###### 语法

WORKDAY(start_date, days, [holidays])

WORKDAY 函数语法具有下列参数：

- **Start_date**  必需。 一个代表开始日期的日期。
- **Days**  必需。 start_date 之前或之后不含周末及节假日的天数。 Days 为正值将生成未来日期；为负值生成过去日期。
- **Holidays**  可选。 一个可选列表，其中包含需要从工作日历中排除的一个或多个日期，例如各种省/市/自治区和国家/地区的法定假日及非法定假日。 该列表可以是包含日期的单元格区域，也可以是由代表日期的序列号所构成的数组常量。

###### 备注

- Microsoft Excel 可将日期存储为可用于计算的序列号。 默认情况下，1900 年 1 月 1 日的序列号是 1，而 2008 年 1 月 1 日的序列号是 39448，这是因为它距 1900 年 1 月 1 日有 39448 天。
- 如果任一参数不是有效日期，则 WORKDAY 返回#VALUE！ 错误值。
- 如果start_date加上天生成无效日期，则 WORKDAY 返回#NUM！ 错误值。
- 如果 days 不是整数，将截尾取整。





#### 逻辑函数

#### 文本函数

#### 统计函数

#### 数学和三角函数

#### 查找引用函数

#### 财务函数



## 图表

### 根据散点找公式

![image-20220121085843926](excel-base/image-20220121085843926.png)



## 技巧

#### 单元格添加下拉选

#### [excel单元格怎么添加百分比进度条](https://link.zhihu.com/?target=https%3A//www.jiachong.com/excel/7545.html)

1. 打开Excel表格，选择要设置进度条的单元格，展开条件格式
2. 展开数据条，选择进度条颜色，就可以实现百分比进度条展示了

#### 检查单元格的一部分是否与特定文本匹配

若要执行此任务，请使用**IF、SEARCH**和**ISNUMBER**函数。

**注意:** **SEARCH**函数不区分大小写。

![IF、ISNUMBER 和 SEARCH 示例](excel-base/e4ea7067-86ce-4f86-9682-1b95bf772729.png)



## 参考资料

[excel技巧-全](https://zh-cn.extendoffice.com/documents/excel)

