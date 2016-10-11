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
>>> keys = 'ABC'
>>> vals = [ ord(k) for k in keys ]
>>> dict(zip(keys, vals))
{'A': 65, 'C': 67, 'B': 66}
>>>
```
