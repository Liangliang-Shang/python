## Environment Variables for Python
1. PYTHONSTARTUP    
Similar to .profile for UNIX Shells. Set PYTHONSTARTUP to the name of a file containing your start-up commands.

+ python start up file to set up Python PS1/PS2    
```Python
$ cat .pythonrc.py
#!/usr/bin/env ipython
import sys
sys.ps1 = 'Run Python: '
sys.ps2 = 'Continue... '
```    
+ export env var PYTHONSTARTUP    
```Bash
$ export PYTHONSTARTUP=.pythonrc.py
```    
+ start python with new PS1/PS2    
```Python
$ python
Python 2.7.3 (default, Dec 18 2012, 13:50:09)
[GCC 4.5.3] on cygwin
Type "help", "copyright", "credits" or "license" for more information.
Run Python: print \
Continue... 'Hello World'
Hello World
Run Python: 
```

2. Zip two lists into a dict
```Python
>>> keys = ('a', 'b', 'c')
>>> vals = (1, 2, 3)
>>> d    = dict(zip(keys, vals))
>>> d
{'a': 1, 'c': 3, 'b': 2}
```

```python
# precise division
from __future__ import division
print 7/4
```

    1.75
    


```python
# nice simple if statement
x, y = 3, 5
less = x if x < y else y
print less
```

    3
    


```python
# string immutable
s = 'abc'
# s[2] = 'a'         # TypeError: 'str' object does not support item assignment
ba = bytearray(s)    # mutable
print ba
ba[2] = 'a'
print ba             # changed to 'aba' from 'abc'
```

    abc
    aba
    


```python
# string slice: [start:end:step]
palindrome = "step on no pets"
print palindrome[::-1]          # reverse the string
print palindrome[:]             # copy the string
print palindrome[-4:]           # the last 4 letters
print palindrome[:4]            # the first 4 letters
print palindrome[::5]           # get letters every 5 letters
print palindrome[1::8]          # get letters every 8 letters 
```

    step on no pets
    step on no pets
    pets
    step
    so 
    to
    


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
    


```python
for i in range(0, 5) + range(2, 8) + range(3, 12) + [2, 2]:
    print ' ' * (40 - 2*i - i//2) + '*'*(4*i + 1 + i)
```

                                            *
                                          ******
                                       ***********
                                     ****************
                                  *********************
                                       ***********
                                     ****************
                                  *********************
                                **************************
                             *******************************
                           ************************************
                                     ****************
                                  *********************
                                **************************
                             *******************************
                           ************************************
                        *****************************************
                      **********************************************
                   ***************************************************
                 ********************************************************
                                       ***********
                                       ***********
    


```python
# comprehension
print [ x for x in range(10) if x % 2 ]              # list comprehension, get a list
print { x for x in range(10) if x % 2 }              # set comprehension, get a set ( {} defines a set)
print { int(x/2): x for x in range(10) if x % 2 }    # dict comprehension, get a dict
print ( x for x in range(10) if x % 2)               # a generator object, O(1)
for i in (x for x in range(10) if x % 2):       
    print i, 
```

    [1, 3, 5, 7, 9]
    set([1, 3, 9, 5, 7])
    {0: 1, 1: 3, 2: 5, 3: 7, 4: 9}
    <generator object <genexpr> at 0x000000000409E708>
    1 3 5 7 9
    


```python
# enumerate, sorted, zip
i = [1, 2, 3, 4]
s = 'abcd'
for index, elem in enumerate(s):                   # enumerate returns a generator producing index/elem
    print index, elem
print zip(i, s)                                    # zip 
for index, elem in zip(i, s):
    print index, elem
print zip(*zip(i, s))                              # 
```

    0 a
    1 b
    2 c
    3 d
    [(1, 'a'), (2, 'b'), (3, 'c'), (4, 'd')]
    1 a
    2 b
    3 c
    4 d
    [(1, 2, 3, 4), ('a', 'b', 'c', 'd')]
    


```python
# paremeter/arguments
def digit2Number(a, b, c):
    return a*100 + b*10 +c
def digit2NumberDefault(a=0, b=0, c=0):
    return a*100 + b*10 + c
print digit2Number(1, 2, 3)                        # three seperate parameters
print digit2Number(*[1, 2, 3])                     # one list parameter, * to unpack it

print digit2NumberDefault(**{'b':2, 'c':3, 'a':1}) # one dict parameter, ** to unpack it
print digit2NumberDefault(**{'b':2, 'c':3})        # like above, and apply a with default value 0
```

    123
    123
    123
    23
    


```python
import numpy as np
npdata = np.genfromtxt('data.csv', skip_header=1, dtype=None, delimiter=',')
```


```python
import pandas as pd
pddata = pd.read_csv('data.csv', header=0, sep=',')
print type(pddata)
pddata.to_csv('data2.tab', index=True, sep=',')
```

    <class 'pandas.core.frame.DataFrame'>
    


```python
d = {'a': 7, 'b': 15, 'c': 33, 'd': 22}
print sorted(d.iteritems(), key=lambda x: x[1], reverse=True)
```

    [('c', 33), ('d', 22), ('b', 15), ('a', 7)]
    




```python
# Context Manager 
class Apollo(object):
        def __init__(self, text):
                self.old = ''
                self.new = text
                print('In __init__: ' + ' '.join([self.old, self.new]))

        def __enter__(self):
                self.old = self.new
                self.new = 'Now __enter__: ' + self.new
                print('In __enter__: ' + ' '.join([self.old, self.new]))

                return self

        def __exit__(self, exec_type, exec_value, traceback):
                self.new = 'Now __exit__: ' + self.old
                print('In __exit__: '  + ' '.join([self.old, self.new]))

with Apollo("Man's small step!") as apollo:
        print('In context: ' + ' '.join([apollo.old, apollo.new]))

print('Out of context: ' + ' '.join([apollo.old, apollo.new]))
```

    In __init__:  Man's small step!
    In __enter__: Man's small step! Now __enter__: Man's small step!
    In context: Man's small step! Now __enter__: Man's small step!
    In __exit__: Man's small step! Now __exit__: Man's small step!
    Out of context: Man's small step! Now __exit__: Man's small step!

