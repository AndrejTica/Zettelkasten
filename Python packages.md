---
date: 2025-06-22
tags:
  - python
---
If you add `__init__.py` into a directory, then python will treat that directory as a package. A package in python is a collection of modules (individual python.py files). 
We can put code into `__init__.py` that we want to be ran when the module is first imported.
Since python 3.3 this file is implicit so we dont need it.
However we can use it to simplify import statements. For that we need to import these modules in the init.py file. Make sure when doing that you do a relative import. For that tell python to look in the current package where the init.py is located. For example: from .math_util import add
The dot tells python to look in this package.

### PYTHONPATH
This is an env variable that tells python in which folder it should look for modules.
The location where the file is ran from is automatically included into the path.
Because of that we wont be able to import modules that are located above the file that is calling the module. To solve this problem, we simply include the root project directory into the pythonpath variable. 

### Package vs Module
They are essentially the same except that a package has the `__path__` attribute.

### References

