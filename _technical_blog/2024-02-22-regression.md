---
title: Multiple variable regression analysis
tags:
  - Knowledge
  - Technique
---

## 是否需要标准化？
答：线性回归不需要。参见：https://blog.csdn.net/shwan_ma/article/details/80154888

其他：
- 如果各个变量之间线性相关，那么系数权重会变得无法解释。参见：https://blog.csdn.net/shwan_ma/article/details/80154888
- 系数权重的绝对值不代表特征重要性。因为系数权重对变量的尺度很敏感，而且如果特征是线性相关的，系数可以从一个特征转移到另一个特征。参见：https://blog.csdn.net/shwan_ma/article/details/80154888
- 