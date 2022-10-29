---
title: 'What is face/edge/cornor connectivity?'
tags:
  - connectivity
  - 3D image
---

## 3D image

![3d box](/images/connectivity_box.jpg)

From the above image (several voxels in 3D image) we can observe that in 3D image, two neighboring pixels could have 3 different relationships: face-connected (red voxel VS gray voxel, distance=1), edge-connected (red voxel VS blue voxel, distance=sqrt(2)) and corner-connected (red voxel VS green voxel, distance=sqrt(3)).


Therefore, given **red** voxel is the object, drawing its border could have 3 different results:  face-connected (only gray voxel is the border, distance=1), edge-connected (gray and blue voxels are the border, where the distance is equal to or less than sqrt(2)) and corner-connected (gray, blue and green voxels are all the border, where the distance is equal to or less than sqrt(3)).


## 2D image

2D image only has face-connected neighbors and edge-connected neighbors. 