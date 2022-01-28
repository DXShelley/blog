---
title: mybatis 源码
tags:
  - programming
  - java
  - frame
  - mybatis
categories:
  - programming
  - java
  - frame
date: 2022-01-24 20:03:14
---

# Mybatis

## 概念

MyBatis 是一款优秀的持久层框架，它支持自定义 SQL、存储过程以及高级映射。MyBatis 免除了几乎所有的 JDBC 代码以及设置参数和获取结果集的工作。MyBatis 可以通过简单的 XML 或注解来配置和映射原始类型、接口和 Java POJO（Plain Old Java Objects，普通老式 Java 对象）为数据库中的记录。

## 整体架构

![MyBatis整体架构](mybatis/MyBatis整体架构.png)



![MyBatis SQL 执行过程](mybatis/MyBatis执行过程-16430281138273.png)

### 基础支持层

- 反射模块：提供封装的反射 `API`，方便上层调用。
- 类型转换：为简化配置文件提供了别名机制，并且实现了 `Java` 类型和 `JDBC` 类型的互转。
- 日志模块：能够集成多种第三方日志框架。
- 资源加载模块：对类加载器进行封装，提供加载类文件和其它资源文件的功能。
- 数据源模块：提供数据源实现并能够集成第三方数据源模块。
- 事务管理：可以和 `Spring` 集成开发，对事务进行管理。
- 缓存模块：提供一级缓存和二级缓存，将部分请求拦截在缓存层。
- `Binding` 模块：在调用 `SqlSession` 相应方法执行数据库操作时，需要指定映射文件中的 `SQL` 节点，`MyBatis` 通过 `Binding` 模块将自定义 `Mapper` 接口与映射文件关联，避免拼写等错误导致在运行时才发现相应异常。

### 核心处理层

- 配置解析：`MyBatis` 初始化时会加载配置文件、映射文件和 `Mapper` 接口的注解信息，解析后会以对象的形式保存到 `Configuration` 对象中。
- `SQL` 解析与 `scripting` 模块：`MyBatis` 支持通过配置实现动态 `SQL`，即根据不同入参生成 `SQL`。
- `SQL` 执行与结果解析：`Executor` 负责维护缓存和事务管理，并将数据库相关操作委托给 `StatementHandler`，`ParmeterHadler` 负责完成 `SQL` 语句的实参绑定并通过 `Statement` 对象执行 `SQL`，通过 `ResultSet` 返回结果，交由 `ResultSetHandler` 处理。



- 插件：支持开发者通过插件接口对 `MyBatis` 进行扩展。

### 接口层

`SqlSession` 接口定义了暴露给应用程序调用的 `API`，接口层在收到请求时会调用核心处理层的相应模块完成具体的数据库操作。



## 参考

[官档](https://mybatis.org/mybatis-3/zh/getting-started.html)

