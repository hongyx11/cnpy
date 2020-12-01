# cnpy with conda package

cnpy is a great library developed by rogersce. [orignal repo](https://github.com/rogersce/cnpy).
This Repo is forked from the original repo and I changed CMakeLists.txt in order to use it as a submodule of your build project.

I also build a conda package so that one can easily install the cnpy as a conda package and detected by cmake.


## Installation
In order to use it in your project, install conda first and do
```bash
conda install -c yhong cnpy
```

In your CMakeLists.txt write
```
find_package(CNPY REQUIRED)
```
