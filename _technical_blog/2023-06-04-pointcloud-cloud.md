---
title: point cloud
tags:
  - Knowledge
---

## Datasets
1. ModelNet
    ModelNet是帶顏色的！ （reference: https://blog.csdn.net/weixin_47142735/article/details/120223827）
    
    .off那个是CAD模型，modelnet40_ply_hdf5_2048是基于原来的采样了一下，只有点的坐标，还有一个版本是带法向量的。

    Reference:    https://blog.csdn.net/qq_41895003/article/details/105431335


    一、介绍

    物体文件格式（.off）文件用于表示给定了表面多边形的模型的几何体。这里的多边形可以有任意数量的顶点。

    普林斯顿形状Banchmark中的.off文件遵循以下标准：

    1、.off文件为ASCII文件，以OFF关键字开头。 

    2、下一行是该模型的顶点数，面数和边数。边数可以忽略，对模型不会有影响(可以为0)。

    3、顶点以x，y，z坐标列出，每个顶点占一行。

    4、在顶点列表之后是面列表，每个面占一行。对于每个面，首先指定其包含的顶点数，随后是这个面所包含的各顶点在前面顶点列表中的索引。

    即以下格式：

    OFF

    顶点数 面数 边数 
    x y z
    x y z
    ...
    n个顶点 顶点1的索引 顶点2的索引 … 顶点n的索引
    ...

    一个立方体的简单例子： 

    COFF
    8 6 0
    -0.500000 -0.500000 0.500000
    0.500000 -0.500000 0.500000
    -0.500000 0.500000 0.500000
    0.500000 0.500000 0.500000
    -0.500000 0.500000 -0.500000
    0.500000 0.500000 -0.500000
    -0.500000 -0.500000 -0.500000
    0.500000 -0.500000 -0.500000
    4 0 1 3 2
    4 2 3 5 4
    4 4 5 7 6
    4 6 7 1 0
    4 1 7 5 3
    4 6 0 2 4

    **Reference:** https://blog.csdn.net/A_L_A_N/article/details/84874463?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task

