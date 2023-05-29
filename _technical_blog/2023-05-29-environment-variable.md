---
title: Python Environments variables
tags:
  - Knowledge
---
环境变量是指当在终端运行命令的时候，从哪些文件夹去找这个命令。比如`python`有很多个也许，用哪一个文件夹里的python呢？就需要沿着环境变量里的所有文件夹一个一个去找，一旦找到就停止，不再继续。

1. check python environment variables:
   1. `echo $PATH`  # in one line
   2. `echo -e ${PATH//:/\\n}`  # line by line
2. python在import的时候是怎样的查找顺序呢？
   1. built-in list 中先找。
   2. 在sys.path中找，这是一个列表，包括下面5部分（有先后顺序！）：
      1. 程序的根目录 (即当前运行python文件的目录。PYTHONPATH环境变量设置的目录
      2. 标准库的目录
      3. 任何能够找到的.pth文件的内容。  # 所以可以把自定义的包路径添加到这个文件里面
      4. 第三方扩展的site-package目录
3. 如何手动添加路径？
   1. 在site-package/*.pth文件中添加
   2. 在python代码最开头添加，如下
   ```
   import sys
   sys.path.append("/home/my/path)
   ```
4. 为什么我的python不是我想要的python?比如我明明在一个python3.8的conda环境里，但是which python显示的并不是pythonn3.8。
   答：这是因为默认的python是从$PATH中的文件夹一个一个按照顺序查找出来的第一个python。通过`echo $PATH`可以验证。这时候需要搞清楚$PATH怎么就被改动了？去看看.bashrc，那里面可能会发现export PATH="your/new/path:$PATH"，大概率就是对$PATH进行改动的代码（新路径插入到开头去了）。注释掉或者调整路径添加的顺序就好了。

Reference:
1. https://blog.csdn.net/qq_27825451/article/details/100552739