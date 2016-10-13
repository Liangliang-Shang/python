## Module   
+ ``` .py ``` file
+ ``` import ```/``` from ... import ... ```    
  Use *import* statement to avoid name space crashes and it is much more readable.   
+ ``` .pyc ``` file    
  Byte-compiled files with the extension ``` .pyc ``` is an intermediate form, which will be much faster since a portion of the processing required in importing a module is already done. And it is platform-independent. These .pyc files are usually created in the same directory as the corresponding .py files.
+ ``` __name__ ```
  Figure out whether the module is being run standalone or being imported.
```Python
if __name__ == '__main__':
    # Run by itself
    pass
else:
    # Being imported from another module
    pass
```
+ ``` dir ```
  Return a list of names defined by an object
```Python
>>> dir()
['__builtins__', '__doc__', '__name__', '__package__']
>>> import sys
# dir() return a list containing sys module name
>>> dir()
['__builtins__', '__doc__', '__name__', '__package__', 'sys']
# get names of attributes in sys module
>>> dir(sys)
['__displayhook__', '__doc__',
'argv', 'builtin_module_names',
'version', 'version_info']
# only few entries shown here
```

## Package
+ The hierarchy of organizing your programs.    
  Variables usually go inside functions. Functions and global variables usually go inside modules. And Modules go inside packages. Packages are just folders of modules with a special ``` __init__.py ``` file.   
```
# directory/file tree of dateutil module
+ dateutil
│  easter.py
│  easter.pyc
│  parser.py
│  parser.pyc
│  relativedelta.py
│  relativedelta.pyc
│  rrule.py
│  rrule.pyc
│  tzwin.py
│  tzwin.pyc
│  __init__.py
│  __init__.pyc
│
├─tz
│      tz.py
│      tz.pyc
│      win.py
│      win.pyc
│      _common.py
│      _common.pyc
│      __init__.py
│      __init__.pyc
│
└─zoneinfo
        dateutil-zoneinfo.tar.gz
        rebuild.py
        rebuild.pyc
        __init__.py
        __init__.pyc
```

## Project
Project: Egyptian_fraction
```Python
+Egyptian_fraction
│  MANIFEST.in
│  README.rst
│  setup.py
│
└─fraction
        fraction.py
        __init__.py
```
+ README.rst
+ Package fraction/Module fraction/fraction.py
+ MANIFEST.in
```Text
include *.py
include README.rst
```
+ setup.py
```Python
#!/usr/bin/env python
"""Egyptian Fraction"""
from setuptools import find_packages, setup

setup(name = 'fraction',
    version = '0.1',
    description = "fraction module.",
    long_description = "A test module for our book.",
    platforms = ["Linux"],
    license = "MIT",
    packages=find_packages()
    )
```
+ build 
```Shell
python setup.py sdist
```
