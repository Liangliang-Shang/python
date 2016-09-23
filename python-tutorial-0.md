# python  
Apress - Begining Python - From Novice to Professional    
[A Byte of Python](https://python.swaroopch.com/basics.html)    
## The Interactive Interpreter
+ *python -V*    
+ *python --help*    
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

## Expressions
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
```Python
>>> pi = 3.14
>>> r  = 1
>>> 2 * pi * r
6.28
```

## Statements  
The difference between a statement and an expression: an expression is something, while a statement does something. 
```Python
>>> pi = 3.14
>>> r  = 1
>>> 2 * pi * r
6.28
>>> print 2 * pi * r
6.28
```

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
```
+ Comments  
Make sure your comments say significant things and don't simply restate what is already obvious from the code. 

## Strings    
+ Single-Quoted/Double-Quoted/Triple-Quoted Strings and Escaping Quotes
  ```Python
>>> 'Hello, world!'                     # Single-Quoted string
'Hello, world!'
>>> 'Let\'s go!'                        # Back-slash to escapte the single quote in a single-quoted string
"Let's go!"
>>> "Let's go!"                         # The single quote could be used as a part of a Double-Quoted string
"Let's go!"
>>> '"Hello, world!" she said'          # vice-versa
'"Hello, world!" she said'
>>> '"Hello, world!" she said'
'"Hello, world!" she said'

# Triple-Quoted string for muliple-line strings, single/double quotes are freely used. 
>>> print '''This is a very long string. 
... It continues here. 
... And it's not over yet. 
... "Hello, world!"
... Still here.'''
This is a very long string. 
It continues here. 
And it's not over yet. 
"Hello, world!"
Still here.
>>> 
```

+ Escaping Sequences & Continuing lines    
  * \', \", \\, \t, \n
  * \
    \ is the last character of the line in python, which means the next line continues the last line.    
  ```Python
>>> print "Hello, \
... world!"
Hello, world!
>>> print \
...     'Hello, world!'
Hello, world!
>>> 1 + 2 + \
...     3 + 4
10
```  
+ Raw Strings  
Raw strings don't treat the backslash as a special character at all. The one thing you can't have in a raw string is a final backslash. A simple way of putting the backslash at the end of a string is: 
  ```Python
>>> print 'Hello,\nworld!'
Hello,
world!
>>> print r'Hello,\nworld!'
Hello,\nworld!
>>> print r'Let\'s go!'
Let\'s go!
>>> print r"This is illegal\"
  File "<stdin>", line 1
    print r"This is illegal\"
                            ^
SyntaxError: EOL while scanning string literal
>>> 
>>> print r"C:\Program Files" '\\'
C:\Program Files\
>>> 
```
+ Concatenating Strings    
  ```Python
>>> "Let's say " '"Hello, world!"'
'Let\'s say "Hello, world!"'
>>> "Hello, " + "world!"
'Hello, world!'
```

+ String Representations, str and repr  
_str_ simply converts a value into a string in some reasonable fashion that will probably be understood by a user, and _repr_, which creates a string that is representation of the value as a legal Python expression. 
  ```Python
>>> "Hello, world!"
'Hello, world!'
>>> 10000L
10000L
>>> print "Hello, world!"
Hello, world!
>>> print 10000L
10000
>>> print repr("Hello, world!")
'Hello, world!'
>>> print repr(10000L)
10000L
```
+ Unicode Strings  
Normal strings in Python are stored internally as 8-bit ASCII, while Unicode strings are stored as 16-bit Unicode. This allows for a more varied set of characters, including special characters from most languages in the world. 
  ```Python
>>> print u'你好！'
你好！
```
