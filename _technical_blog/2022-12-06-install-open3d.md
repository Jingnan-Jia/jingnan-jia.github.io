---
title: 安装open3d
tags:
  - Python
---


## It took me a long time to install open3d

At first, I tried to install it on cluster, but enven it successfully installed, it raised ERROR during importing it in Python. This is because it require [glibc higher than 2.18 or 2.27 (newest version)](https://github.com/isl-org/Open3D/issues/5178). But my cluster has glibc of version 2.17.

Then, I tried to install it on my own workstation but still faied because my own workstation does not have a good GPU I think.

Finally, I installed it on my own PC using "pip install open3d" in a brand new conda environment.

