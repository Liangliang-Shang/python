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
>>> hello('universe', 'Greetings')              # two parameters with diff orders to those above, parameter order matters
universe, Greetings!
>>> hello(name='Gumby')                         # one key word parameter and default the other parameter
Hello, Gumby!
>>> hello(name='Gumby', greeting='Evening')     # two keyword parameters
Evening, Gumby!
>>> hello(greeting='Evening', name='Gumby')     # two keyword parameters with diff order to those above, and it does not matter
Evening, Gumby!
```
