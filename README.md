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
