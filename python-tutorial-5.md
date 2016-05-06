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
['Mr. Gumby', 'Mrs. Thing']      # names does get changed! two variables are refertring to the same list
>>> n = names[:]                 # using slicing on a sequence, got a copy of the list
>>> n is names                   # two separate lists
False
>>> n == names                   # they are equal
True
```
+ Keyword Parameters and Defaults  
```Python
>>> def hello(greeting='Hello', name='world'):
...     print '%s, %s!' % (greeting, name)
... 
>>> hello()                                     # using default parameters 
Hello, world!
>>> hello('Greetings')                          # default the name parameter as parameter order matters
Greetings, world!
>>> hello('Greetings', 'universe')              # two parameters
Greetings, universe!
>>> hello('universe', 'Greetings')              # two parameters and parameter order matters
universe, Greetings!
>>> hello(name='Gumby')                         # one key word parameter and default the other parameter
Hello, Gumby!
>>> hello(name='Gumby', greeting='Evening')     # two keyword parameters
Evening, Gumby!
>>> hello(greeting='Evening', name='Gumby')     # two keyword parameters and parameter order does not matter
Evening, Gumby!
>>> def greeting(name, greeting='Hello', punctuation='!'):    # combining positional and keyword parameters
...     print '%s, %s%s' % (greeting, name, punctuation)
... 
>>> greeting('Mars')                     # requiring the positional parameter come first, default the others
Hello, Mars!
>>> greeting('Mars', 'Howdy')            # default the third parameter
Howdy, Mars!
>>> greeting('Mars', 'Howdy', '...')     # No default! Positions matter
Howdy, Mars...
>>> greeting('Mars', punctuation='.')    # default greeting parameter
Hello, Mars.
>>> greeting('Mars', greeting='Top of the morning to ya')  # default the third parameter
Top of the morning to ya, Mars!
>>> greeting()                           # the first parameter is required as no default
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: greeting() takes at least 1 argument (0 given)
```
+ Collecting Parameters  
```Python
>>> def printParams(title, *params):    # the star means "Gather up the rest of the positional parameters
...     print title
...     print params
... 
>>> printParams('Params:', 1, 2, 3)
Params:
(1, 2, 3)                               # Gather up  1, 2, 3 into params tuple
>>> def printKeywordParams(**params):   # Gather up keyword parameters 
...     print params
... 
>>> printKeywordParams(x=1, y=2, z=3)
{'y': 2, 'x': 1, 'z': 3}
>>> def printAllParams(x, y, z=3, *pospar, **keypar):
...     print x, y, z
...     print pospar
...     print keypar
... 
>>> printAllParams(1, 2, 3, 5, 6, 7, foo=1, bar=2)
1 2 3
(5, 6, 7)
{'foo': 1, 'bar': 2}
```
```Python
>>> def printPosParams(*params):
...     for index, param in enumerate(params):
...             print index, param
... 
>>> l = ('a', 'b')         # already have parameters into a list l
>>> printPosParams(l)      # take l as the whole one, rather than all the elements in the list as params
0 ('a', 'b')
>>> printPosParams(*l)     # distribute l into params, it is what we want!
0 a
1 b
>>> def printKeywordParams(**params):
...     for key in params: 
...             print key, params[key]
... 
>>> d = {'a': 'A', 'b': 'B'}    # already package a='A', b='B' keyword params into a dict d
>>> printKeywordParams(**d)     # using two stars both  when defining and calling the function
a A
b B
```

