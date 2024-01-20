---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume/
---

{% include base_path %}

<!-- <a href='/files/Jingnan_cv_2022.pdf'>CV PDF (not updated frequently)</a> -->


<!-- <a href='/files/Jingnan_cv_2022_Chinese.pdf'>中文简历下载</a> -->

Education
======
* Ph.D in Leiden University, Leiden, the Netherlands
  * Deep learning in medical image analysis
  * Supervisor: Berend Stoel and Marius Staring
  * 2019-2023 (expected)
  
* M.S. in Xidian University, Xian, China 
  * Electromagnetic field and microwave technology
  * Supervisor: Yong-Chang Jiao
  * 2016-2019
  
* B.S. in Taiyuan University of Technology, Taiyuan, China
  * Applied physics
  * 2011-2015
  

  


Work experience
======
* Summer 2018: Research Assistant
  * Dongguan University of Technology
  * Duties included: Poisoning Attack in Deep Neural Network

  
Skills
======
* Expertise
  * Segmentation (UNet, nnUNet), classification (VGG, ResNet, ConvNeXt), regression
  * Point cloud (PointNet, PointNet++, PointNeXt)
  * Deep supervision
  * multi-task learning
  * semi-supervised learning
  * Multi-processing/-threading
  * Multi-GPU training

* Programming language
  * Python
  * MATLAB
  * Bash

* Deep learning platform
  * PyTorch
  * Keras
  * TensorFlow
  
* Other tools:
Linux, Vim, Latex, Git, Jekyll, Sphinx, reStructuredText, MarkDown, Docker, MLFlow, MONAI, SimpleITK, Lighting, Ignite, TorchIO, PyCharm, VS Code, SSH, WSL, etc.


Achievements
=================
* Finalist of best student paper award for SPIE: Medical Imaging 2022. [Cerificate of award](/files/spie_certificate.pdf)
* Top 3 of at the UCL Medical Image Compting Summer School (MedICSS 2021). [Certificate of participation](/files/MedICSS2021_certificate_Participant_Jingnan-Jia.pdf). [Certificate of award](/files/MedICSS2021_certificate_ProjectMerit_Jingnan-Jia.pdf).   
* SPIE: Medical Imaging 2022 Student Conference Support (up to $1000 for airfare and/or lodging as well as a registration fee waiver).


Other activieies
==================
* Reviewer for Medical Image Analysis (MedIA), The IEEE International Symposium on Biomedical Imaging (ISBI) 2022, 2023.
* Student member of SPIE, ISBI and IEEE.
* Own and still maintain an open sourse package: [seg-metrics](https://pypi.org/project/seg-metrics/) for medical image segmentation metrics calculation. Downloads per month is over [500](https://pypistats.org/packages/seg-metrics).

* Contribute to open source packages like [MONAI](https://github.com/Project-MONAI/MONAI) and [MLflow](https://github.com/mlflow/mlflow). I proposed `Issues` and created `Pull requests` merged to the main branches of them.

Publications
======
  <ul>{% for post in site.publications %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Talks
======
  <ul>{% for post in site.talks %}
    {% include archive-single-talk-cv.html %}
  {% endfor %}</ul>
  
Teaching
======
  <ul>{% for post in site.teaching %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
