# python  
Apress - Begining Python - From Novice to Professional    
[A Byte of Python](https://python.swaroopch.com/basics.html)    
[Elements of Python Style](https://github.com/amontalenti/elements-of-python-style)    
[pym py2](http://pymbook.readthedocs.io/en/py2/variablesanddatatypes.html)
## The Interactive Interpreter
```Shell
$ python -V
```
```Shell
$ python --help
```
+ Environment Variables    
  * **PYTHONSTARTUP**    
  * **PYTHONPATH**    
```Shell
# Set PYTHONSTARTUP to the name of a file executed on interactive startup (no default)
# Similar to .profile for UNIX Shells. 
$ export PYTHONSTARTUP=.pythonrc.py

# Set module search path to directories separated by ':' and prefixed to the default ones. 
# The result is sys.path
$ export PYTHONPATH=~/lib:$PYTHONPATH

$ cat .pythonrc.py
#!/usr/bin/env python
# reset the prime and secondary prompt for python in the interactive mode. 
import sys
sys.ps1 = 'Run Python: '
sys.ps2 = 'Continue... '
$ python
Python 2.7.3 (default, Dec 18 2012, 13:50:09)
[GCC 4.5.3] on cygwin
Type "help", "copyright", "credits" or "license" for more information.
Run Python: print \             # the first prompt changed (\ is to continue the print statement line). 
Continue... 'Hello World'       # the secondary prompt changed. 
Hello World
Run Python: print sys.path[0:4]
['', '/home/lshang/lib', '/home/lshang', '/usr/lib/python27.zip']
```

## Literal Constants
a number like 5, 1.23, or a string like 'This is a string' or "It's a string!"

## Operators & Expressions
+ +, -, *, /, %, **, //, <, >, <=, >=, ==, !=, not, and, or
```Python
>>> 1 + 9
10
>>> 1/2
0
>>> from __future__ import division  # command-line switch: -Qnew for such division
>>> 1/2
0.5
```
+  Large Integers  
   A long (or long integer) is written with and L at the end.  
```Python
>>> 100000000000000000000
100000000000000000000L
```
+  Hexadecimals and octals  
   The first digit in both of these is zero.  
```Python
>>> 0xAF
175
>>> 010
8
```

## Variables  
A variable is basically a name that represents (or refers to) some value.  Variable names can consist of letters, digits and underscore characters(_). A variable can't begin with a digit. 
+ Identifiers(Names)
```
identifier ::= (letter|"_") (letter | digit | "_")*
letter ::= lowercase | uppercase
lowercase ::= "a"..."z"
uppercase ::= "A"..."Z"
digit ::= "0"..."9"
``` 
+ Keyword
```
and       del      from      not   while
as        elif     global    or    with
assert    else     if        pass  yield
break     except   import    print
class     exec     in        raise
continue  finally  is        return
def       for      lambda    try
``` 

+ Data Type
  * number
  * string
  * object    
    Everything is an object in Python including number, string, functions.    

## Statements  
The difference between a statement and an expression: an expression is something, while a statement does something. 
```Python
>>> pi = 3.14                 # statement, assign 3.14 to pi
>>> r  = 1                    # statement, assign 1 to r
>>> 2 * pi * r                # expression, evaluated and printed in the interactive mode
6.28
>>> print 2 * pi * r          # statement, print out the evaluation
6.28
>>> a, b = 45, 54             # multiple assignments in a single line
>>> a, b
(45, 54)
>>> a, b = b, a               # swap!!!
>>> a, b
(54, 45)
```
+ if/elif/else    
+ while 
```Python
>>> name = ''
>>> while not name:
...     print 'Hello?'
...     name = raw_input("What's your name? ")
... else:
...     print 'Hello, ' + name
...
Hello?
What's your name?
Hello?
What's your name? John Smith
Hello, John Smith
```
+ for ... in    
Iterate over a sequence of objects. 
+ continue    
Skip the rest statements of the current loop block and continue to the next iteration of the loop    
+ break    
Break out/stop execution of a loop statment    

## Getting Input from the User  
_input_ assumes that what you enter is a valid Python expression. 
```Python
>>> input("x: ")
x: 0.618
0.618
>>> raw_input("x: ")
x: 0.618
'0.618'
```

## Functions  
```Python
>>> round(1.0/2.0)
1.0
>>> pow(2, 3)
8
```

## Modules  
```Python
>>> import math
>>> math.sqrt(100)
10.0
```

## Python Script/File  
+ shebang  
```Python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
```
+ Comments  
Make sure your comments say significant things and don't simply restate what is already obvious from the code. 
+ Indentation    
Use four spaces for indentation.    
