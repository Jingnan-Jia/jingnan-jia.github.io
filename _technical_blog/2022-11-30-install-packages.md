---
title: 安装Python包的N种方式
tags:
  - Knowledge
---


# 安装Python包的N种方式

## 通过pip或者conda安装已经发布的包
### 最经典最常用的方式：pip install [package_name]
绝大部分的Python包可以通过`pip install [package_name]`来安装。因为绝大部分Python包都会被上传到[PyPi](https://pypi.org/).

### conda install [package_name]
对于`conda`的用户，另一种常用的方式是`conda install [package_name]`。但是其实并不是所有的包都会被上传到`conda`所维护的服务器上。对于Python包的开发者而言，第一选择肯定是传到Python官方的包托管平台PyPi上，如果还有时间或者想进一步推广自己的包的话，会选择再把自己的包上传到conda的包托管平台。而且conda有两个包托管的源：Anaconda公司自己维护的源（包质量比较稳定，更新较慢）和社区维护的conda-forge（更新较快）。

## 安装本地的包
一般我们自己写好了Python包之后，如果只给自己用，一般可以通过两种方式：
### 相对导入。比如：`from .. import [module_name]`
### 绝对导入之把包的根目录加载到环境变量。
* 用Python导入：
  ```
    import sys
    sys.path.append(r'E:\src\ttlayer')
    sys.path.insert(0,r'E:\src\ttlayer')
  ```

* 在Linux里导入

  方法1：
  ```
  export PATH=/home/uusama/mysql/bin:$PATH
  # 或者把PATH放在前面
  export PATH=$PATH:/home/uusama/mysql/bin
  ```
  **注意事项**：
  生效时间：立即生效
  生效期限：当前终端有效，窗口关闭后无效
  生效范围：仅对当前用户有效
  配置的环境变量中不要忘了加上原来的配置，即$PATH部分，避免覆盖原来配置

  方法2：
  通过修改用户目录下的`~/.bashrc`文件进行配置.在最后一行加上：
  `export PATH=$PATH:/home/uusama/mysql/bin`
  **注意事项**：
  生效时间：使用相同的用户打开新的终端时生效，或者手动source ~/.bashrc生效
  生效期限：永久有效
  生效范围：仅对当前用户有效
  如果有后续的环境变量加载文件覆盖了PATH定义，则可能不生效

### 绝对导入之把包进行安装
1. python setup.py install
2. python setup.py develop
3. pip install .
4. pip install -e .

What is the difference between the above 4 commands?
Answer: [This link](https://stackoverflow.com/questions/19048732/python-setup-py-develop-vs-install?noredirect=1&lq=1)

5. conda develop .
