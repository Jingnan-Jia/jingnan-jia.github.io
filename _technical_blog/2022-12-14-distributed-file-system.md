---
title: Distributed file system
tags:
  - Knowledge
---

## 直连存储（DAS）：
存储和数据直连，拓展性、灵活性差。
为了扩展，将文件和服务分离，通过网络连接——

## 中心化存储（NAS、SAN）：
设备类型丰富，通过网络互连，具有一定的拓展性，但是受到控制器能力限制，拓展能力有限。同时，设备到了生命周期要进行更换，数据迁移需要耗费大量的时间和精力。

## 分布式存储：
通过网络使用企业中的每台机器上的磁盘空间，并将这些分散的存储资源构成一个虚拟的存储设备，数据分散的存储在企业的各个角落。

## 主流分布式文件存储系统
目前主流的分布式文件系统有：GFS、HDFS、Ceph、Lustre、MogileFS、MooseFS、FastDFS、TFS、GridFS等。

Reference:
1. https://zhuanlan.zhihu.com/p/350096155
