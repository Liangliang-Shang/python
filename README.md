# python  
Apress - Begining Python - From Novice to Professional

## The Interactive Interpreter
```Shell
20160308 22:14:06 lshang@elemos:/home/lshang 
$ python
Python 2.7.3 (default, Jun 22 2015, 19:33:41) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> print "Hello, world!"
Hello, world!
>>> 
```

## Numbers and Expressions
```Python
>>> 1 + 9
10
>>> 1/2
0
>>> from __future__ import division
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
+ Single-Quoted Strings and Escaping Quotes  
```Python
>>> 'Hello, world!'
'Hello, world!'
>>> 'Let\'s go!'
"Let's go!"
>>> "Let's go!"
"Let's go!"
>>> '"Hello, world!" she said'
'"Hello, world!" she said'
>>> '"Hello, world!" she said'
'"Hello, world!" she said'
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

+ Long Strings, Raw Strings, and Unicode
```Python
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
+ Unicode Strings  
Normal strings in Python are stored internally as 8-bit ASCII, while Unicode strings are stored as 16-bit Unicode. This allows for a more varied set of characters, including special characters from most languages in the world. 
```Python
>>> print u'你好！'
你好！
```

*A data structure is a collection of data elements (such as numbers or characters -- or even other data structures) that is structured in some way, for example, by numbering the elements.*  

*Python has six built-in types of sequences: lists, tuples, strings, Unicode strings, buffer objects, xranges objects.*  

## Sequences  
```Python
>>> edward = ['Edward Gumby', 42]
>>> john   = ['John Smith', 50]
>>> database = [edward, john]
>>> database
[['Edward Gumby', 42], ['John Smith', 50]]
```
+ Indexing  
All elements in a sequence are numbered - from zero and upwards.  
_A string is just a sequence of characters._  
When you use a negative index, Python counts from the right, that is, from the last element. The last element is at position -1 (not -0, as that would be the same as the first element): 
```Python
>>> greeting = 'Hello'
>>> greeting[0]
'H'
>>> greeting[-1]
'o'
>>> 'Hello'[1]
'e'
>>> third = raw_input('Year: ')[2]
Year: 2016
>>> third
'1'
```
+ Slicing  
Slicing to access ranges of elements
```Python
>>> numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> numbers[3:6]
[4, 5, 6]
>>> numbers[7:20]
[8, 9, 0]
>>> numbers[-3:-1]
[8, 9]
>>> numbers[-3:0]
[]
>>> numbers[-3:]
[8, 9, 0]
>>> numbers[:3]
[1, 2, 3]
>>> numbers[:]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> numbers[0:10:2]
[1, 3, 5, 7, 9]
>>> numbers[::4]
[1, 5, 9]
>>> numbers[10:0:-2]
[0, 8, 6, 4, 2]
>>> numbers[5::-2]
[6, 4, 2]
>>> numbers[:5:-2]
[0, 8]
>>>
```
+ Adding Sequences
```Python
>>> [1, 2, 3] + [4, 5, 6]
[1, 2, 3, 4, 5, 6]
>>> 'Hello, ' + 'world!'
'Hello, world!'
>>> [1, 2, 3] + 'world!'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate list (not "str") to list
>>> 
```
+ Multiplication  
Multiplying a sequence by a number x creates a new sequence where the original sequence is repeated x times: 
```Python
>>> 'Abc' * 3
'AbcAbcAbc'
>>> [1, 2, 3] * 5
[1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3]
```
+ None, Empty Lists, and Initialization
```Python
>>> emptyList = []
>>> sequence = [None] * 10
>>> emptyList
[]
>>> sequence
[None, None, None, None, None, None, None, None, None, None]
```
+ Membership  
```Python
>>> numbers
[1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> 1 in numbers
True
>>> 10 in numbers
False
>>> 'P' in 'Python'
True
```
+ Length, Minimum, and Maximum
```Python
>>> numbers
[1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> len(numbers)
10
>>> min(numbers)
0
>>> max(numbers)
9
```

## Lists
