Abstraction  
Abstraction and Structure  
## Function    
Give a name to a block statements (*define a function*) and allow you to run that block using the specified name anywhere and any times(*call the function*). Build-in functions: *len*/*range*
+ *def*    
  Start the definition of a function
+ Identifier Name    
  Name a function
+ a pair of parentheses    
  Enclose some names of variables (*parameters*)    
+ the final colon    
  End the line of defining the function.
+ Indented block of statements
  * *pass*    
    Indicate an empty block of statements.     
  * *return*    
    Return from the function/Break out of the function.  Every function implicitly contains a *return None* statement at the end unless you have written your own return statement.
```Python
# Identifier Name: sayHelloWorld
# No parameters 
def sayHelloWorld():
    # Block belonging to the function
	print "Hello World!"             # Indented block of statements
# End of the function

sayHelloWorld()
sayHelloWorld()
```

### DocStrings    
```Python
>>> def square(x):
...     'Calculates the square of the number x.'
...     return x*x
... 
>>> square.__doc__        # __doc__ is a function attribute. 
'Calculates the square of the number x.'
# Press the q key to exit *help*
>>> help(square)
Help on function square in module __main__:

square(x)
    Calculates the square of the number x.
(END)
```

### Function Parameters    
Parameters are specified within the pair of parentheses in the function definition, separated by commas.    
+ Local variables
Inside a function definition, variable names are local to the function. They are not related in any way to other variables with the same names used outside the function.     
+ global
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
Only those parameters which are at the end of the parameter list can be given default argument values.
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

## Scoping
```Python
>>> x = 1
>>> scope = vars()        # equivalent to locals(), return a dict containing variables/values
>>> scope['x']
1
>>> scope['x'] += 1
>>> x
2
```
This sort of dictionary is called a namespace or scope.  
In addition to the global scope, each function call creates a new one: 
```Python
>>> def foo():    # a new function, a new namespace for the block inside foo
...     x = 42    # local variable that doesn't affect the x in the outer (global) scope
... 
>>> x = 1
>>> foo()
>>> x
1
>>> def combine(parameter): print parameter + external    # external is not defined 
... 
>>> external = 'berry'
>>> combine('Shrub')
Shrubberry
>>> def combine(parameter):     # the global variable parameter is shadowed by the local one
...     print parameter + globals()['parameter']  # Got the global one 
... 
>>> parameter = 'berry'
>>> combine('Shrub')
Shrubberry
```
+ Rebinding Global Variables
```Python
>>> x = 1
>>> def change_global():
...     global x
...     x = x + 1
... 
>>> change_global()
>>> x
2
```
## Recursion   
A useful recursive function usually consists of the following parts:  
+ A base case (for the smallest possible problem) when the function returns a value directly  
+ A recursive case, which contains one or more recusrive calls on smaller parts of the problem    
    
### Factorial    
```Python
>>> def factorial(n):
...     if n == 1:
...             return 1
...     else: 
...             return n * factorial(n-1)
... 
>>> factorial(5)
120
```
### Power
```Python
>>> def power(x, n):
...     if n == 0:
...             return 1
...     else:
...             return x * power(x, n-1)
... 
>>> power(2, 3)
8
```
