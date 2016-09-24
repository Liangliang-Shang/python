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
```
+ Comments  
Make sure your comments say significant things and don't simply restate what is already obvious from the code. 
+ Indentation    
Use four spaces for indentation.    

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
    if \ is the last character of the line in python, which means the next line continues the last line.    

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
Raw strings don't treat the backslash as a special character at all. The one thing you can't have in a raw string is a final backslash. It is very helpful when you are writing a Windows file system path or in a regular expression. 

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
>>> print r"C:\Program Files" '\\'               # to avoid double back slash to escapte \
C:\Program Files\
>>> 
```

+ Unicode Strings  
Normal strings in Python are stored internally as 8-bit ASCII, while Unicode strings are stored as 16-bit Unicode. This allows for a more varied set of characters, including special characters from most languages in the world.    

```Python
>>> print u'你好！'
你好！
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
+ Immutable    
Once you create a string, you cannot change it anymore. 
+ Format    
str.format method is much more simpler and eligant than string concatenation, and  the conversion to string would be done automatically
```python
# format string
print '{}, {}'.format('abc', 'xyz')                # position matters
print '{}, {}'.format('xyz', 'abc')                # position matters
print '{0}, {1}, {0}'.format('abc', 'xyz')         # position reusable
```

    abc, xyz
    xyz, abc
    abc, xyz, abc
    


```python
# format string (continued)
print '{first}, {last}'.format(last='abc', first='xyz')             # keyword parameters
print '{first}, {last}, {first}'.format(last='abc', first='xyz')    # keyword reusable
```

    xyz, abc
    xyz, abc, xyz
    


```python
# format string (continued)
import this
print '{self.i}{self.c}'.format(self=this)          # class/object/module
```

    25!
    


```python
# format string (continued)
l = ('a', 'b', 'c')
print '{0[2]}-{0[1]}-{0[0]}'.format(l)              # format a list
d = {'a': 'x', 'b': 'y', 'c': 'z'}
print '{0[a]},{0[b]},{0[c]}'.format(d)              # format a dict
```

    c-b-a
    x,y,z
    


```python
# format numbers/with style? 
pi = 3.1415926
print '{:0<9}'.format('{:.2f}'.format(pi))
x  = 23
print '{0:0<17} = {1:0>17}'.format(pi, pi)               # position:padding{align:^|<|>}length
d  = 127
print '{0:d}(d) = {0:b}b = {0:o}o = {0:x}x'.format(d)    # decimal, binary, oct, hex
print '{0:0<17} = {0:,}'.format(pi * 1000000)            # 314,159.26
```

    3.1400000
    3.141592600000000 = 000000003.1415926
    127(d) = 1111111b = 177o = 7fx
    3141592.600000000 = 3,141,592.6

```Python
>>> print('{0}{1: ^72}{0}'.format('+', 'README'))         # fill with ' ' with the text centered in 72 width
+                                 README                                 +
```
