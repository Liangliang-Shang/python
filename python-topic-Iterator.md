## Iterator
Require to support two methods    
+ *```__iter__```*    
Returns the iterator object itself    
+ *```next```*    
Returns the next value from the iterator. If there is no more items to return, then it should raise *StopIteration* exception    
```Python
class Counter(object):
	def __init__(self, low, high):
		self.current	= low
		self.high		= high

	def __iter__(self):
		'return itself as an iterator object'
		return self

	def next(self):
		'return the next value till current is lower than high'
		if self.current > self.high:
			raise StopIteration
		else:
			self.current += 1
			return self.current - 1
```
```Python
>>> c = Counter(5, 10)
>>> for i in c:
...     print i,
...
5 6 7 8 9 10
>>> c = Counter(0, 1)
>>> next(c)
0
>>> next(c)
1
>>> next(c)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 11, in next
    raise StopIteration
StopIteration
>>> next(c)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 11, in next
    raise StopIteration
StopIteration
>>> iterator = iter(Counter(5, 10))
>>> while True:
...     try:
...             x = iterator.next()
...             print x,
...     except StopIteration as e:
...             break
...
5 6 7 8 9 10
```

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
# precise division
from __future__ import division
print 7/4
```

    1.75


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
# enumerate, sorted, zip
i = [1, 2, 3, 4]
s = 'abcd'
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

