---
title: 'Full tutorial for a complete python project'
tags:
  - python
  - Tutorial
---

- Pycharm clone project (optional)
- Pycharm remote interpreter
- Pycharm remote deployment
- Pycharm line separator change from CRLF to LF: file -> file properties -> line separator
- Structure Overview
LICENSE
    - README.md
    - Requirements.txt
    - Setup.py
    - Test (directory)
    - Src / projecct_name (directory)
    - Scripts (directory)
    - Docs (directory)
    - .github (directory)
    - .coveragerc

- Guideline: https://github.com/elsewhencode/project-guidelines 
- Creat a project name.
- Create README.md using this [template](https://github.com/elsewhencode/project-guidelines/blob/master/README.sample.md).
- Create a [logo](https://www.canva.com/design/DAEsDqa08sc/gQz2ekQVFDtvTBqJbScDTA/edit) for your project
- Put your logo into ./docs/images/logo.png and show it in README.md, width=200 align=’center’  
- Create setup.py and LICENSE. Setup.py: 
    ```python
    import setuptools
    
    with open("README.md", "r") as fh:
        long_description = fh.read()
    
    setuptools.setup(
        name="socsa", # Replace with your own username
        version="0.0.1",
        author="Jingnan",
        author_email="jiajingnan2222@gmail.com",
        description="A package to compute analysis solar cell stability testing results.",
        long_description=long_description,
        long_description_content_type="text/markdown",
        url="https://github.com/Jingnan-Jia/socsa",
        packages=setuptools.find_packages(),
        classifiers=[
            "Programming Language :: Python :: 3",
            "License :: OSI Approved :: MIT License",
            "Operating System :: OS Independent",
        ],
        python_requires='>=3.6',
        install_requires=[],
    )
    
    ```
- Write module python files in ‘project_name’ directory.
- Create directory of ‘tests’, ‘docs’, ‘scripts’ and ‘project_name’. ‘Scripts’ will save main code to run experiments, ‘project_name’ will save functions/ packages.
    - When recalling relative functions/modules, always use such absolute import method:  “import project_name.module_name …”
- Write script files in ‘scripts’.

    When recalling relative functions/modules, always use such absolute import method:  “import project_name.module_name …”, 
but make sure to add this sentence at the first of the script: 
    ```
    import sys
    sys.path.append("..")
    ```
    This can make sure the script can find these modules. Otherwise, a ‘module not found’ error would occur.
- Create a ‘data’ directory here to save dataset
- Write .coveragerc
    ```python
    # .coveragerc to control coverage.py
    [run]
    omit =
        */site-packages/*
        */dist-packages/*
        */distutils/*
        tests/*

  ```
  
- Write test files in ‘tests’
    Note, to avoid import Error, we need:
        1. Test files should call absolute modules’ name directly.
        2. Create a runner.py with the following contents:
        
        ```python
        test_dir = os.path.dirname(os.path.realpath(__file__))
        package_dir = os.path.dirname(test_dir)
        sys.path.append(package_dir)
        ```
- Write a test runner to run all test files

    When recalling relative functions/modules, always use such absolute import method:  “import project_name.module_name …”, 

    There are two methods to run all test files:
    Command method: 
    ```bash
    python -m unittest discover
    In python file:
    ```
    or `runner.py`:
    
    ```python
    loader = unittest.TestLoader()
    tests = loader.discover('.', pattern='test_*.py')
    testRunner = unittest.runner.TextTestRunner()
    test_results = testRunner.run(tests)
    ```
  
	Similarly, there are two methods to run code coverage:
    Command method:`coverage run -m unittest discover`, or In `runner.py` file:
    ```python
        if COV_FLAG:
            cov = coverage.coverage()
            cov.start()
    
        loader = unittest.TestLoader()
        tests = loader.discover('.', pattern='test_*.py')
        testRunner = unittest.runner.TextTestRunner()
        test_results = testRunner.run(tests)
    
        if COV_FLAG:
            cov.stop()
            cov.save()
            # 命令行模式展示结果
            cov.report()
            # 生成HTML覆盖率报告
            cov.html_report(directory='./tests/covhtml')
            cov.xml_report(outfile='./tests/cov_report.xml')
    ```
    
    Here, we use the second method for unittest and coverage report.
    
    Create a runner.py here with the following content:
    
    ```python
    import unittest
    import coverage
    COV_FLAG = True
    if __name__ == "__main__":
        if COV_FLAG:
            cov = coverage.coverage()
            cov.start()
    
        loader = unittest.TestLoader()
        tests = loader.discover('.', pattern='test_*.py')
        testRunner = unittest.runner.TextTestRunner()
        test_results = testRunner.run(tests)
    
        if COV_FLAG:
            cov.stop()
            cov.save()
            # 命令行模式展示结果
            cov.report()
            # 生成HTML覆盖率报告
            cov.html_report(directory='./tests/covhtml')
            cov.xml_report(outfile='./tests/cov_report.xml')
    
        if test_results.wasSuccessful():  # used in github actions to make sure actions fail when tests fails
            exit(0)
        else:
            exit(1)
    ```
- Create requirements.txt
- Write .gitignore
- Write github actions for auto test and coverage report
    In `.github/workflow/test_and_coverage.yml`：
    ```python
    name: Test
    on: [push]
    jobs:
      Explore-GitHub-Actions:
        runs-on: ubuntu-latest
        steps:
          - name: Check out repository code
            uses: actions/checkout@v2        
          - run: echo "💡 The ${{ github.repository }} repository has been cloned to the runner."
          - name: Start test
            run: |
              pip install -r requirements.txt
              python ./tests/runner.py
              bash <(curl -s https://codecov.io/bash) -f ./tests/cov_report.xml
              echo "Succesfully! Cheers!"
    ```
  
- Get test and code coverage badge
    - goto https://app.codecov.io/gh/Jingnan-Jia
    - login with your github account
    - select repositories from ‘not yet setup’ 
    - copy the token to the github’s project’s setting’s secret. 
    - add the [following code](https://docs.codecov.com/docs/supported-languages 
    and: https://github.com/codecov/example-python ) to ‘.github/workflows/test_and_coverage.yml’
    ```python
    - name: "Upload coverage to Codecov"
    uses: codecov/codecov-action@v2
    with:
      fail_ci_if_error: true  # optional
      token: ${{ secrets.CODECOV_TOKEN }} # not required for public repos
    ```
    - In README.md, add the [following badge code](https://about.codecov.io/product/feature/badges/):
    ```python
    [![codecov](https://codecov.io/gh/Jingnan-Jia/socsa/branch/master/graph/badge.svg?token=Z808SDKUFQ)](https://codecov.io/gh/Jingnan-Jia/socsa)
    ![example workflow](https://github.com/Jingnan-Jia/socsa/actions/workflows/test_and_coverage.yml/badge.svg?branch=master)
 
    ```
    You can the branch, otherwise, using the default branch.
    More details about getting badges: https://github.com/dwyl/repo-badges 

- Write document in ‘docs’ with sphinx
    - sphinx-quickstart docs
    - sphinx-build -b html docs/source/ docs/build/html(equal to: make html) # optional
    - Install this theme: `pip install sphinx-rtd-theme`
    - 
    - Change config.py  # very important !!!
    ```python
    html_theme = 'sphinx_rtd_theme'
    sys.path.insert(0, os.path.abspath('../..'))
    sys.path.insert(0, os.path.abspath('../../project_name'))
    ```
    - Try to make html at first: `make html`
   
- Put docs to network
    Note: Be patient. The online docs would be updated after 1-2 hours once you re-built the docs.
    - ‘sphinx-apidoc -o docs/source project_name --force’ locally to generate files in ‘source’ directory at first.
    - edit the index.rst to combine all docs together.
    - Then look the below steps:
    - Create a file `.readthedos.yml`: 
    ```python
    # .readthedocs.yml
    # Read the Docs configuration file
    # See https://docs.readthedocs.io/en/stable/config-file/v2.html for details
    
    # Required
    version: 2
    
    # Build documentation in the docs/ directory with Sphinx
    sphinx:
      configuration: docs/source/conf.py
    
    # Build documentation with MkDocs
    #mkdocs:
    #  configuration: mkdocs.yml
    
    # Optionally build your docs in additional formats such as PDF and ePub
    # formats: all
    
    # Optionally set the version of Python and requirements required to build your docs
    python:
      version: 3.7
      install:
        - requirements: docs/requirements.txt
    #  system_packages: true
    
    
    build:
      image: stable

    ```

    - Then create another file `docs/requirements.txt`:
    ```python
    # Defining the exact version will make sure things don't break
    sphinx
    sphinx_rtd_theme
    readthedocs-sphinx-search
    coverage==5.5
    parameterized==0.8.1
    pandas==1.0.5
    numpy==1.21.1
    tqdm==4.61.2
    ```
    Follow [This tutorial](https://docs.readthedocs.io/en/stable/tutorial/) is very easy.
- Add documentation badge
    Click the [link](https://readthedocs.org/projects/socsa/) and look at the right direction.
