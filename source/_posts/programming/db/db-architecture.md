---
title: 数据库读写分离与分库分表
tags:
  - db
  - architecture
  - high
categories:
  - programming
  - db
date: 2021-12-22 09:00:27
---

# # 数据库架构设计

## 读写分离

### 原理

### 实现

#### 1. 数据库搭建主从服务器，一主一从或一主多从

2. 主负责写操作，从负责读操作（读写分离）
3. 主通过复制将数据同步至从，所有主机存储了一样的全部数据
4. web服务器分别读从和写主

### 使用场景

#### 并发量大，读多写少，实时性要求不高

#### 读写分离不是银弹，并不是一有性能问题就上读写分离，而是应该先优化，例如优化慢查询，调整不合理的业务逻辑，引入缓存查询等只有确定系统没有优化空间后才考虑读写分离集群

### 引入问题

#### 主从复制延迟

##### 写操作后路由读请求

##### 重读：读取从失败再读一次主

##### 按业务路由读请求（关键业务读写主，其他读从）

#### 分配机制

##### 客户端程序代码封装实现

###### Sharding-JDBC

定位为轻量级Java框架，在Java的JDBC层提供的额外服务。 它使用客户端直连数据库，以jar包形式提供服务，无需额外部署和依赖，可理解为增强版的JDBC驱动，完全兼容JDBC和各种ORM框架

###### 淘宝TDDL

淘宝根据自身业务需求研发了 TDDL （ Taobao Distributed Data Layer ）框架，主要用于解决 分库分表场景下的访问路由（持久层与数据访问层的配合）以及异构数据库之间的数据同步 ，它是一个基于集中式配置的 JDBC DataSource 实现，具有分库分表、 Master/Salve 、动态数据源配置等功能

##### 服务端中间件封装

###### MySQL Router

####### 基于MySQL Router可以实现读写分离，故障自动切换，负载均衡，连接池等功能。

###### Atlas是由平台部基础架构团队开发维护的一个基于MySQL协议的数据中间层项目。它是在mysql-proxy的基础上，对其进行了优化，增加了一些新的功能特性

## 分库分表

### 数据切分

#### 关系型数据库本身比较容易成为系统瓶颈，单机存储容量、连接数、处理能力都有限。当单表的数据量达到1000W或100G以后，由于查询维度较多，即使添加从库、优化索引，做很多操作时性能仍下降严重。此时就要考虑对其进行切分了，切分的目的就在于减少数据库的负担，缩短查询时间。

#### 垂直切分

##### 垂直切分常见有垂直分库和垂直分表两种

##### 垂直分库就是根据业务耦合性，将关联度低的不同表存储在不同的数据库。做法与大系统拆分为多个小系统类似，按业务分类进行独立划分。与"微服务治理"的做法相似，每个微服务使用单独的一个数据库

##### 垂直分表是基于数据库中的"列"进行，某个表字段较多，可以新建一张扩展表，将不经常用或字段长度较大的字段拆分出去到扩展表中。

在字段很多的情况下（例如一个大表有100多个字段），通过"大表拆小表"，更便于开发与维护，也能避免跨页问题，MySQL底层是通过数据页存储的，一条记录占用空间过大会导致跨页，造成额外的性能开销。
另外数据库以行为单位将数据加载到内存中，这样表中字段长度较短且访问频率较高，内存能加载更多的数据，命中率更高，减少了磁盘IO，从而提升了数据库性能。

##### 优缺点

###### 解决业务系统层面的耦合，业务清晰

与微服务的治理类似，也能对不同业务的数据进行分级管理、维护、监控、扩展等
高并发场景下，垂直切分一定程度的提升IO、数据库连接数、单机硬件资源的瓶颈

###### 部分表无法join，只能通过接口聚合方式解决，提升了开发的复杂度

分布式事务处理复杂
依然存在单表数据量过大的问题（需要水平切分）

#### 水平切分（分库分表）

##### 当一个应用难以再细粒度的垂直切分，或切分后数据量行数巨大，存在单库读写、存储性能瓶颈，这时候就需要进行水平切分了。

##### 水平切分分为库内分表和分库分表，是根据表内数据内在的逻辑关系，将同一个表按不同的条件分散到多个数据库或多个表中，每个表中只包含一部分数据，从而使得单个表的数据量变小，达到分布式的效果

##### 库内分表只解决了单一表数据量过大的问题，但没有将表分布到不同机器的库上，因此对于减轻MySQL数据库的压力来说，帮助不是很大，大家还是竞争同一个物理机的CPU、内存、网络IO，最好通过分库分表来解决。

##### 优缺点

###### 不存在单库数据量过大、高并发的性能瓶颈，提升系统稳定性和负载能力

应用端改造较小，不需要拆分业务模块

###### 跨分片的事务一致性难以保证

跨库的join关联查询性能较差
数据多次扩展难度和维护量极大

##### 数据分片规则

###### 根据数值范围

####### 按照时间区间或ID区间来切分

####### 优缺点

######## 单表大小可控
天然便于水平扩展，后期如果想对整个分片集群扩容时，只需要添加节点即可，无需对其他分片的数据进行迁移
使用分片字段进行范围查找时，连续分片可快速定位分片进行快速查询，有效避免跨分片查询的问题。

######## 热点数据成为性能瓶颈

###### 根据数值取模

####### 简单取模/一致性hash算法

####### 优缺点

######## 数据分片相对比较均匀，不容易出现热点和并发访问的瓶颈

######## 后期分片集群扩容时，需要迁移旧的数据（使用一致性hash算法能较好的避免这个问题）
容易面临跨分片查询的复杂问题。比如上例中，如果频繁用到的查询条件中不带cusno时，将会导致无法定位数据库，从而需要同时向4个库发起查询，再在内存中合并数据，取最小集返回给应用，分库反而成为拖累。

### 引入问题

#### 事务一致性问题

##### 分布式事务

###### 当更新内容同时分布在不同库中，不可避免会带来跨库事务问题。跨分片事务也是分布式事务，没有简单的方案，一般可使用"XA协议"和"两阶段提交"处理。

###### 分布式事务能最大限度保证了数据库操作的原子性。

但在提交事务时需要协调多个节点，推后了提交事务的时间点，延长了事务的执行时间。
导致事务在访问共享资源时发生冲突或死锁的概率增高。
随着数据库节点的增多，这种趋势会越来越严重，从而成为系统在数据库层面上水平扩展的枷锁

##### 最终一致性

###### 对于那些性能要求很高，但对一致性要求不高的系统，往往不苛求系统的实时一致性，只要在允许的时间段内达到最终一致性即可，可采用事务补偿的方式。

与事务在执行中发生错误后立即回滚的方式不同，事务补偿是一种事后检查补救的措施，
一些常见的实现方法有：对数据进行对账检查，基于日志进行对比，定期同标准数据来源进行同步等等。事务补偿还要结合业务系统来考虑。

#### 跨节点关联查询 join 问题

##### 全局表，也可看做是"数据字典表"，就是系统中所有模块都可能依赖的一些表，为了避免跨库join查询，可以将这类表在每个数据库中都保存一份。这些数据通常很少会进行修改，所以也不担心一致性的问题

##### 一种典型的反范式设计，利用空间换时间，为了性能而避免join查询。

例如：订单表保存userId时候，也将userName冗余保存一份，这样查询订单详情时就不需要再去查询"买家user表"了。
但这种方法适用场景也有限，比较适用于依赖字段比较少的情况。
而冗余字段的数据一致性也较难保证，就像上面订单表的例子，买家修改了userName后，是否需要在历史订单中同步更新呢？这也要结合实际业务场景进行考虑

##### 在系统层面，分两次查询，第一次查询的结果集中找出关联数据id，然后根据id发起第二次请求得到关联数据。最后将获得到的数据进行字段拼装。

##### 关系型数据库中，如果可以先确定表之间的关联关系，并将那些存在关联关系的表记录存放在同一个分片上，那么就能较好的避免跨分片join问题。在1:1或1:n的情况下，通常按照主表的ID主键切分。如下图所示：

#### 跨节点分页、排序、函数问题

##### 跨节点多库进行查询时，会出现limit分页、order by排序等问题。

分页需要按照指定字段进行排序，当排序字段就是分片字段时，通过分片规则就比较容易定位到指定的分片；
当排序字段非分片字段时，需要先在不同的分片节点中将数据进行排序并返回，然后将不同分片返回的结果集进行汇总和再次排序，最终返回给用户

##### 在使用Max、Min、Sum、Count之类的函数进行计算的时候，也需要先在每个分片上执行相应的函数，然后将各个分片的结果集进行汇总和再次计算，最终将结果返回

#### 全局主键避重问题

##### UUID

##### 结合数据库维护主键ID表

##### Snowflake分布式自增ID算法（雪花算法-强依赖机器时钟）

###### 参考业界较为成熟的解法：Leaf——美团点评分布式ID生成系统

，并考虑到了高可用、容灾、分布式下时钟等问题

#### 数据迁移、扩容问题

##### 如果采用数值范围分片，只需要添加节点就可以进行扩容了，不需要对分片数据迁移。如果采用的是数值取模分片，则考虑后期的扩容问题就相对比较麻烦。

### 考虑切分

#### 不到万不得已不用轻易使用分库分表这个大招，避免"过度设计"和"过早优化"。

分库分表之前，不要为分而分，先尽力去做力所能及的事情，
例如：升级硬件、升级网络、读写分离、索引优化等等。当数据量达到单表的瓶颈时候，再考虑分库分表。

#### 随着业务发展，需要对某些字段垂直拆分

#### 鸡蛋不要放在一个篮子里。

在业务层面上垂直切分，将不相关的业务的数据库分隔，因为每个业务的数据量、访问量都不同，不能因为一个业务把数据库搞挂而牵连到其他业务。
利用水平切分，当一个数据库出现问题时，不会影响到100%的用户，每个库只承担业务的一部分数据，这样整体的可用性就能提高。

### 支持分库分表中间件

#### sharding-jdbc（当当）

TSharding（蘑菇街）

Atlas（奇虎360）

Cobar（阿里巴巴）

MyCAT（基于Cobar）需重点了解，深挖

Oceanus（58同城）

Vitess（谷歌）

### 参考

#### 数据库分布式架构扫盲——分库分表（及银行核心系统适用性思考）

分库分表的思想

水平分库分表的关键步骤以及可能遇到的问题

从原则、方案、策略及难点阐述分库分表

Leaf——美团点评分布式ID生成系统

数据库水平切分架构实践-【架构师之路】公众号

## 分支主题