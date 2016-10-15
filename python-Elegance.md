# Elegance of python    

## built-in
+ if ... else ...
```Python
>>> x, y = 3, 5
>>> less = x if x < y else y
>>> print less
3
```
+ enumerate
```Python
>>> for index, char in enumerate('ABC'):
...     print index, char
...
0 A
1 B
2 C
```
+ zip
```Python
>>> keys = 'ABC'
>>> vals = [ ord(k) for k in keys ]
>>> dict(zip(keys, vals))
{'A': 65, 'C': 67, 'B': 66}
>>>
```
+ map
```Python
>>> map(chr, xrange(65, 68))
['A', 'B', 'C']
>>> [ chr(i) for i in xrange(65, 68) ]    # equivalently list comprehension
['A', 'B', 'C']
```
+ with
```Python
>>> with open('HelloWorld.py') as f:
...     f.read()
...
```
+ dict->setdefault
```Python
>>> d = dict()
>>> d.setdefault('A', []).append('America')
>>> d.setdefault('A', []).append('Africa')
>>> d
{'A': ['America', 'Africa']}
```
## Comprehension
```Python
>>> [ chr(i) for i in xrange(65, 69) ]          # list comprehension
['A', 'B', 'C', 'D']
>>> { chr(i): i%65 for i in xrange(65, 69) }    # dict comprehension
{'A': 0, 'C': 2, 'B': 1, 'D': 3}
>>> { i%2 for i in xrange(65, 69) }             # set comprehension
set([0, 1])
```
