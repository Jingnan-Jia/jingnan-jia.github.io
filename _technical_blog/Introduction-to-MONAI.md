---
title: 'Introduction to MONAI'
date: 2022-9-10
tags:
  - Python packages
  - Tutorial

---

The first time I touched MONAI is from a challenge: [COVID-19 Lung CT Lesion Segmentation Challenge - 2020](https://covid-segmentation.grand-challenge.org/).
The official originizer provided a [banchmark](https://github.com/Project-MONAI/tutorials/tree/main/3d_segmentation/challenge_baseline) implemented by MONAI.

I found MONAI is very helpful and have been using it untill now.

## What is MONAI?
[MONAI](https://github.com/Project-MONAI/MONAI) is a PyTorch-based, open-source framework for deep learning in healthcare imaging, part of PyTorch Ecosystem. 


## Features

- flexible pre-processing for multi-dimensional medical imaging data;
- compositional & portable APIs for ease of integration in existing workflows;
- domain-specific implementations for networks, losses, evaluation metrics and more;
- customizable design for varying user expertise;
- multi-GPU data parallelism support.


## Installation

To install [the current release](https://pypi.org/project/monai/), you can simply run:

```bash
pip install monai
```

Please refer to [the installation guide](https://docs.monai.io/en/latest/installation.html) for other installation options.

## Getting Started

[MedNIST demo](https://colab.research.google.com/drive/1wy8XUSnNWlhDNazFdvGBHLfdkGvOHBKe) and [MONAI for PyTorch Users](https://colab.research.google.com/drive/1boqy7ENpKrqaJoxFlbHIBnIODAs1Ih1T) are available on Colab.

Examples and notebook tutorials are located at [Project-MONAI/tutorials](https://github.com/Project-MONAI/tutorials).

Technical documentation is available at [docs.monai.io](https://docs.monai.io).

## Model Zoo
[The MONAI Model Zoo](https://github.com/Project-MONAI/model-zoo) is a place for researchers and data scientists to share the latest and great models from the community.
Utilizing [the MONAI Bundle format](https://docs.monai.io/en/latest/bundle_intro.html) makes it easy to [get started](https://github.com/Project-MONAI/tutorials/tree/main/model_zoo) building workflows with MONAI.