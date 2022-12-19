---
title: YAML for data split
tags:
  - Knowledge
---

## Why do we need YAML for data split?

Normally I used a fixed random seed to split dataset. However, I found that my dataset has been slightly and gradually updated with the development of the project. 

For instance, in the latter experiments, I found that some patients should be excluded. Then should I re-train all the previous expreiments again? if not, how to ensure the following experiments use the same training/validation/testing data with the previous experiment? (The same seed for different lenth of patient list will lead to very different data split)

So let's use a YAML file to split dataset so that we can always have the almost same split for training/validation/testing data.


