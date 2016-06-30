

```python
'''
init a dict / an empty dict
'''
( dict(), {} )
```




    ({}, {})




```python
'''
init a dict with the key list and/or their default values
'''
({}.fromkeys(['name', 'age']), dict.fromkeys(['name', 'age'], '(unknown)'))
```




    ({'age': None, 'name': None}, {'age': '(unknown)', 'name': '(unknown)'})




```python
'''
init a dict with items/keyword parameters
'''
( dict([('name', 'Gumby'), ('age', 42)]), dict(name='Gumby', age=42))
```




    ({'age': 42, 'name': 'Gumby'}, {'age': 42, 'name': 'Gumby'})




```python
'''
form the two lists with the same length into a dict
'''
I = [0, 1, 2, 3]
S = '''abcd'''
( dict(zip(I, S)), { i:s for (i, s) in zip(I, S) }, { I[i]: S[i] for i in range(len(I)) } )
```




    ({0: 'a', 1: 'b', 2: 'c', 3: 'd'},
     {0: 'a', 1: 'b', 2: 'c', 3: 'd'},
     {0: 'a', 1: 'b', 2: 'c', 3: 'd'})




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


