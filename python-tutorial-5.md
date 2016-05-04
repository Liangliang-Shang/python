Abstraction  
Abstraction and Structure  
## Function and docstring  
```Python
>>> def square(x):
...     'Calculates the square of the number x.'
...     return x*x
... 
>>> square.__doc__        # __doc__ is a function attribute. 
'Calculates the square of the number x.'
>>> help(square)
Help on function square in module __main__:

square(x)
    Calculates the square of the number x.
(END)
```

## The Magic of Parameters 
```Python
>>> def try_to_change(n):
...     n = 'Mr. Gumby'
...
>>> name = 'Mrs. Entity'
>>> try_to_change(name)
>>> name                 # name does not get changed!
'Mrs. Entity'
>>> def change(n):
...     n[0] = 'Mr. Gumby'
...
>>> names = ['Mrs. Entity', 'Mrs. Thing']
>>> change(names)
>>> names
['Mr. Gumby', 'Mrs. Thing']                # names does get changed! two variables are refertring to the same list
>>> n = names[:]                           # using slcing on a sequence, got a copy of the list
>>> n is names                             # two separate lists
False
>>> n == names                             # they are equal
True
```
