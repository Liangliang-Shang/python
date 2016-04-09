## Dictionary  
> Telephone numbers (and other numbers that may contain leading zeros) should be represented as strings of digits - not integers.  
> Octal numbers are written with an initial zero.  

```Python
>>> names = ['Alice', 'Beth', 'Cecil', 'Dee-Dee', 'Earl']
>>> numbers = ['2341', '9102', '3158', '0142', '5551']
>>> numbers[names.index('Cecil')]
'3158'
```

+ Dictionary Syntax  
> Dictionaries consist of pairs (called items) of keys and their corresponding values.  
> Each key is separated from its value by a colon (:)  
> the items are separated by commas  
> the whole thing is enclosed in curly braces.  
> An empty dictionary without any items is written with just two curly braces, like this: {}.  

```Python
>>> phonebook = {'Alice': '2341', 'Beth': '9102', 'Cecil': '3258'}
>>> phonebook['Cecil']
'3258'
```

+ The dict Function  
> The dict function isn't really a function at all. It is a type, just like list, tuple, and str.  
```Python
>>> items = [('name', 'Gumby'), ('age', 42)]          # sequences of (key, value) pairs
>>> d = dict(items)
>>> d
{'age': 42, 'name': 'Gumby'}
>>> d['name']
'Gumby'
>>> d = dict(name='Gumby', age=42)                    # using keyword arguments
>>> d
{'age': 42, 'name': 'Gumby'}
```

+ Basice Dictionary Operations  

```Python
>>> d
{'age': 42, 'name': 'Gumby'}
>>> len(d)
2
>>> d['name']
'Gumby'
>>> 'name' in d
True
>>> del d['name']
>>> d
{'age': 42}
```

```Python
>>> x = []
>>> x[6] = 'Foobar'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list assignment index out of range
>>> x = [None] * 7
>>> x[6] = 'Foobar'
>>> x
[None, None, None, None, None, None, 'Foobar']
>>> x = {}
>>> x[42] = 'Foobar'
>>> x
{42: 'Foobar'}
```

+ String Formatting with Dictionaries  
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

+ Dictionary Methods
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
