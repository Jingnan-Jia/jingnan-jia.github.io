---
title: 'AI可解释性'
tags:
  - AI
---

## 简介
CNN通常由一些卷积块（卷积层+激活层+池化层）和全连接层组成。
![](https://rpmarchildon.com/wp-content/uploads/2018/06/RM-CNN-Schematic-1.jpg)

CNN的可解释性可以通过以下几种方式进行。

1. 特征图可视化
   通过直接展示中间层的特征图（一般要归一化到0-256之间），观察经过每一层卷积之后图片的变化。比如下面2张[图](https://arxiv.org/pdf/1311.2901.pdf)中前几层是纹理，后几层是更高级的综合性的信息
   ![](https://miro.medium.com/max/638/0*qgBQt9dMbUtntbpn.jpg)
   ![](/images/explain_cn.jpg)   
   **问题1：** 为什么上面2张图中后面的特征图反而像素更高？难道不是后面的特征图的尺寸更小，像素更低吗？
   **答案1：** 因为这并不是直接的特征图可视化，而是DeConv: 把中间层的特征，一层一层反传到输入端口，使得特征图的尺寸逐步放大到和输入图片相同 (原文："map these activities back to the input pixel space, showing what input pattern originally caused a given activation in the feature maps")。

   **问题2** 这个DeConvnet生成的图，输入是什么？是最后一个卷积块的输出（全连接层之前）？
   **答案2** 论文原话："To examine a given convnet activation, we set all other activations in the layer to zero and pass the feature maps as input to the attached deconvnet layer".





## CAM Series 类别激活图系列
### CAM
### Grad-CAM

## RAM回归激活图

## Saliency 显著性

## Occlusion sensitifity 遮挡敏感度
![](https://lh5.googleusercontent.com/acHqfkoiS23CKlhdqyB4fvjJ86PNEcT0GUOxRfpCDPo4nO5o_YRBkOR4hrErBcryGUiK5L5xAmFy8Lbae8IAPihcVPeKiMMT9mD_MPRl_C2I4LNtaKgYN0FyNVnLBIMJXLq0CwIs)


参考文献：
1. https://rpmarchildon.com/wp-content/uploads/2018/06/RM-CNN-Schematic-1.jpg
2. https://miro.medium.com/max/638/0*qgBQt9dMbUtntbpn.jpg
3. https://blog.csdn.net/fu6543210/article/details/80407911
4. https://www.tinymind.net.cn/articles/3dedb66b996232
5. https://hackmd.io/@machine-learning/ByaTE80BI#ZFNetDeconvNet-Summary-and-Implementation
6. https://datahacker.rs/028-visualization-and-understanding-of-convolutional-neural-networks-in-pytorch/