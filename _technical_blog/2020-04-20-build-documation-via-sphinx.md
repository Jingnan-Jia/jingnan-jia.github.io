---
title: 'How to build documentation via sphinx?'
tags:
  - Python
  - Tutorial
---

Automatically build documation for your python project.

1. sphinx-apidoc -o source ../ssc_scoring -f
1. Make clean
1. Make html
1. (stand at project root directory) sphinx-quickstart docs
1. (stand at project root directory) 
sphinx-build -b html docs/source/ docs/build/html (equal to: make html)
1. Cd docs
1. Make html
