---
title: 'Automatically Generate Documentation for your Project/Package'
tags:
  - Python
  - Documentation
  - Sphinx
  - reStructuredText
  - Tutorial
---


Once we built a project/package, we need to tell the users how to use it. Normally we could write a manual. But with the update of the code, the manual needs to be updated at the same time. How to synthesize the update of the manual? We need to use 
some automatic tools to automate the pipeline. This blog will tell you how to build your Documentation automatically.

The following contents are from [this blog](https://blog.csdn.net/lixiaomei0623/article/details/120530642) which seems clearer. I recommend to see the original blog directly for Chinese readers.

## Using Sphinx to automatically generate documentation
The following steps are summarized from the [official documentation of sphinx](https://www.sphinx-doc.org/en/master/usage/quickstart.html).

1. Install Sphinx: `pip install -U sphinx`
2. [In the `package/project root directory`] run `mkdir docs` to create a directory for the documentation generation.
3. [In the `docs` directory], run `sphinx-apidoc -o source ../<project_name> -f`
4. [In the `docs` directory], run `sphinx-quickstart`. Enter your information. I recommended you to select to **seperate** the source and build directory. After that, you will get two directories and two `make` files.
5. Specify the source code path in `doc/source/conf.py`:
  ```
  import os
  import sys
  sys.path.insert(0, os.path.abspath('../../src'))
  ```
5. Add extensions to `doc/source/conf.py`:
  ```
  extensions = [
    'sphinx.ext.autodoc',
    'sphinx.ext.napoleon',
    'sphinx.ext.doctest',
    'sphinx.ext.intersphinx',
    'sphinx.ext.todo',
    'sphinx.ext.coverage',
    'sphinx.ext.mathjax',
    ]
  ```
5. [In the `docs` directory], run `make html`. If raising `ERROR: Unknown directive type "automodule`, See [here](https://stackoverflow.com/questions/13516404/sphinx-error-unknown-directive-type-automodule-or-autoclass) to fix it.
6. Write some contents. Look at [this doc](https://github.com/Jingnan-Jia/socsa/blob/master/docs/source/index.rst) which added `tutorial`, `experiment_summary` and `api` to the `index.rst`, which will load the three `.rst` files. So we need to write something to the three files.





References:
1. https://www.sphinx-doc.org/en/master/usage/quickstart.html
2. https://blog.csdn.net/lixiaomei0623/article/details/120530642

