# Elegance of python    

## built-in
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
>>> s = 'ABC'
>>> v = [ ord(c) for c in s ]
>>> d = dict(zip(s, v))
>>> d
{'A': 65, 'C': 67, 'B': 66}
```
