
```python
'''
set/get default value
'''
( {}.setdefault('someKey', 'default'), {}.get('nonExistentKey', 'N/A') )
```




    ('default', 'N/A')




```python
'''
update a dict with some dict
and return None
'''
d = {}
( d.update({'someKey': 'someValue'}), d)
```




    (None, {'someKey': 'someValue'})




```python
'''
sort a dict by key/value
'''
d = {'a': 7, 'b': 15, 'c': 33, 'd': 22}
( sorted(d.iteritems(), key=lambda x: x[0], reverse=False),    # sort the dict by key 
  sorted(d.iteritems(), key=lambda x: x[1], reverse=True) )    # sort the dict by value
```




    ([('a', 7), ('b', 15), ('c', 33), ('d', 22)],
     [('c', 33), ('d', 22), ('b', 15), ('a', 7)])




```python

```


```python

```
