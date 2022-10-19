---
title: 'Develop and release your python package'
tags:
  - Python
  - Tutorial

---

## How to update my code in pypi?
```bash
python setup.py sdist bdist_wheel
twine upload dist/*
```
