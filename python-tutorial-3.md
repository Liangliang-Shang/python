## Dictionary  
> Telephone numbers (and other numbers that may contain leading zeros) should be represented as strings of digits - not integers.  
> Octal numbers are written with an initial zero.  

```Python
>>> names = ['Alice', 'Beth', 'Cecil', 'Dee-Dee', 'Earl']
>>> numbers = ['2341', '9102', '3158', '0142', '5551']
>>> numbers[names.index('Cecil')]
'3158'
```
Dictionary: unordered set of key: value pairs where keys are unique. 

### Dictionary Syntax  
> Dictionaries consist of pairs (called items) of keys and their corresponding values.  
> Each key is separated from its value by a colon (:)  
> the items are separated by commas  
> the whole thing is enclosed in curly braces.  
> An empty dictionary without any items is written with just two curly braces, like this: {}.  

```Python
>>> phonebook = {'Alice': '2341', 'Beth': '9102', 'Cecil': '3258'}
>>> phonebook['Cecil']                                   # Access to/Retrieve the value from a dict with its key
'3258'
>>> phonebook['Dina'] = '7625'                           # Simplely add one more key/value pair into a dict
>>> phonebook
{'Beth': '9102', 'Alice': '2341', 'Dina': '7625', 'Cecil': '3258'}
>>> del phonebook['Beth']
>>> phonebook
{'Alice': '2341', 'Dina': '7625', 'Cecil': '3258'}
```

+ The dict Function  
  The dict function isn't really a function at all. It is a type, just like list, tuple, and str.  
```Python
>>> keys = ('a', 'b', 'c')
>>> vals = (1, 2, 3)
>>> d    = dict(zip(keys, vals))                      # Zip two lists to make a dict
>>> d
{'a': 1, 'c': 3, 'b': 2}
>>> items = [('name', 'Gumby'), ('age', 42)]          # lists of tuples: (key, value) pairs
>>> d = dict(items)
>>> d
{'age': 42, 'name': 'Gumby'}
>>> d = dict(name='Gumby', age=42)                    # use keyword arguments
>>> d
{'age': 42, 'name': 'Gumby'}
```

### Basice Dictionary Operations  

```Python
>>> d
{'age': 42, 'name': 'Gumby'}
>>> len(d)
2
>>> 'name' in d
True
```

```Python
>>> x = []
>>> x[6] = 'Foobar'                            # x is a empty list, index 6 is out of range.
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list assignment index out of range
>>> x = [None] * 7                             # x is a list with length：7 and with None as placeholder
>>> x[6] = 'Foobar'
>>> x
[None, None, None, None, None, None, 'Foobar']
>>> x = {}
>>> x[42] = 'Foobar'
>>> x
{42: 'Foobar'}
```

### String Formatting with Dictionaries  
```Python
>>> phonebook
{'Beth': '9102', 'Alice': '2341', 'Cecil': '3258'}
>>> "Cecil's phone number is %(Cecil)s." % phonebook
"Cecil's phone number is 3258."
>>> template = '''<html>
... <head><title>%(title)s</title></head>
... <body>
... <h1>%(title)s</h1>
... <p>%(text)s</p>
... </body>
... </html>'''
>>> data = {'title': 'My Home Page', 'text': 'Welcome to my home page!'}
>>> print template % data
<html>
<head><title>My Home Page</title></head>
<body>
<h1>My Home Page</h1>
<p>Welcome to my home page!</p>
</body>
</html>
```

### Dictionary Methods
  + clear
  + copy
  + fromkeys
  + get
  + has_key
  + items and iteritems
  + keys and iterkeys
  + pop 
  + popitem
  + setdefault
  + update
  + values and itervalues
```Python
'''
init a dict / an empty dict
'''
>>> dict(), {}
({}, {})
'''
init a dict with the key list and/or their default values
'''
>>> {}.fromkeys(['name', 'age'])
{'age': None, 'name': None}
>>> dict.fromkeys(['name', 'age'])
{'age': None, 'name': None}
>>> dict.fromkeys(['name', 'age'], '(unknown)')
{'age': '(unknown)', 'name': '(unknown)'}
'''
init a dict with items/keyword parameters
'''
( dict([('name', 'Gumby'), ('age', 42)]), dict(name='Gumby', age=42))
form the two lists with the same length into a dict
'''
I = [0, 1, 2, 3]
S = '''abcd'''
( dict(zip(I, S)), { i:s for (i, s) in zip(I, S) }, { I[i]: S[i] for i in range(len(I)) } )
```
```Python
>>> d = {}
>>> d['name'] = 'Gumby'
>>> d['age'] = 42
>>> d
{'age': 42, 'name': 'Gumby'}
>>> returned_value = d.clear()
>>> d
{}
>>> print returned_value
None
>>> x = {}
>>> y = x                       # x and y now refer to the same dictionary
>>> x['key'] = 'value'
>>> y
{'key': 'value'}
>>> x = {}                      # "blank out" x by assigning a new, empty dictionary
>>> y                           # doesn't affect y at all
{'key': 'value'}
>>> x = y                       # x and y now refer to the same dictionary again
>>> x
{'key': 'value'}
>>> y
{'key': 'value'}
>>> x.clear()                   # remove all the elements 
>>> y                           # y is then also empty afterward.  
{}
```
```Python
>>> x = {'username': 'admin', 'machines': ['foo', 'bar', 'baz']}
>>> y = x.copy()  # return a new dictionary with the same key-value pairs(a shallow copy, the values themselves are the same, not copies)
>>> x
{'username': 'admin', 'machines': ['foo', 'bar', 'baz']}
>>> y
{'username': 'admin', 'machines': ['foo', 'bar', 'baz']}
>>> y['username'] = 'mlh'
>>> y['machines'].remove('bar')
>>> y
{'username': 'mlh', 'machines': ['foo', 'baz']}
>>> x
{'username': 'admin', 'machines': ['foo', 'baz']}
>>> from copy import deepcopy
>>> d = {}
>>> d['names'] = ['Alfred', 'Bertrand']
>>> c = d.copy()
>>> dc = deepcopy(d)
>>> from copy import deepcopy
>>> d = {}
>>> d['names'] = ['Alfred', 'Bertrand']
>>> c = d.copy()
>>> dc = deepcopy(d)
```

```Python
>>> d = {}
>>> print d['name']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'name'
>>> print d.get('name')               # No exception using get function!!!
None
>>> d.get('name', 'N/A')              # Return the default value. 
'N/A'
>>> d['name'] = 'Eric'
>>> d.get('name')
'Eric'
```
```Python
>>> d = {}
>>> d.has_key('name') == True # check whether a dictionary has a given key, equivalent to k in d
False
>>> d['name'] = 'Eric'
>>> d.has_key('name') == True
True
```
```Python
>>> d = {'name': 'lynn', 'age': 30}
>>> d.items()
[('age', 30), ('name', 'lynn')]
>>> it = d.iteritems()
>>> it
<dictionary-itemiterator object at 0x7fa620110f18>
>>> list(it)    # convert the iterator to a list
[('age', 30), ('name', 'lynn')]
```
```Python
>>> d = {'x': 1, 'y': 2}
>>> d.pop('x')            # return the value corresponding to a given key, and then remove the key-value pair from the dictionary 
1
>>> d
{'y': 2}
```
```Python
>>> d = {'x': 1, 'y': 2, 'z': 3}
>>> d.popitem()           # pops off a random item, may be useful if you want to remove and process the items one by one
('y', 2)
```
```Python
>>> language = {}
>>> language.setdefault('names')    # The default is optional; if it is left out, None is used
>>> language
{'names': None}
>>> language = {}
# Set the value corresponding to the given key if it is not already in the dictionary
>>> language.setdefault('names', []).append('Python')   
>>> language
{'names': ['Python']}
>>> language.setdefault('names', []).append('Perl')
>>> language
{'names': ['Python', 'Perl']}
```

```Python
>>> d = {'x': 1, 'y': 2, 'z': 3}
>>> x = {'x': 21}
>>> d.update(x)
>>> d
{'y': 2, 'x': 21, 'z': 3}
```

## Set
Unordered collections of simple objects.
```Python
>>> set('banana')                                          # unique the characters in 'banana'
set(['a', 'b', 'n'])
>>> bric = set(['Brazil', 'Russia', 'India', 'China'])
>>> bric
set(['Brazil', 'China', 'India', 'Russia'])
>>> 'China' in bric
True
>>> 'USA' in bric
False
>>> bri = bric.copy()
>>> bri.remove('China')
>>> bric.issuperset(bri)
True
>>> bric - bri                                             # element in bric but not in bri
set(['China'])
>>> bri & bric                                             # element in both bric and bri
set(['Brazil', 'India', 'Russia'])
>>> bric | bri                                             # element in either bric or bri
set(['Brazil', 'China', 'India', 'Russia'])
>>> bric ^ bri                                             # element in bric or bri but not both
set(['China'])
>>> bri.add('China')
>>> bri
set(['Brazil', 'India', 'China', 'Russia'])
```
## Iteration
+ Iterate over a sequence(list/string/tuple)
```Python
>>> for index, value in enumerate(['a', 'b', 'c']):
...     print index, value
...
0 a
1 b
2 c
```
+ Iterate over two sequences at the same time
```Python
>>> str1 = 'abc'
>>> str2 = 'xyz'
>>> for s1, s2 in zip(str1, str2):
...     print s1, s2
...
a x
b y
c z
```
+ Iterater over a dict: 
```Python
>>> d = {'a': 'x', 'c': 'z', 'b': 'y'}
>>> for key, val in d.items():
...     print key, val
...
a x
c z
b y
>>> for key, val in d.iteritems():
...     print key, val
...
a x
c z
b y
```
