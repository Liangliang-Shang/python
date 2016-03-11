## Working with Strings  
All the standard sequence operations (indexing, slicing, multiplication, membership, length, minimum, and maximum) work with strings, however, strings are immutable. All kinds of item or slice assignments are illegal:  
```Python
>>> quote = 'To be or not be'
>>> quote[0:3]
'To '
>>> quote[0:3] = 2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
```
+ Formatting
The string formatting operator: the percent(%) sign. 
```Python
>>> format = "Hello, %s. %s enough for ya?"
>>> values = ('world', 'Hot')
>>> print format % values
Hello, world. Hot enough for ya?
>>> from math import pi
>>> print format % pi
Pi with three decimals: 3.142
```
  + TEMPLATE STRINGS
```Python
>>> from string import Template
>>> s = Template('$x, glorious $x!')
>>> s.substitute(x='slurm')
'slurm, glorious slurm!'
>>> s = Template("It's ${x}tastic!")
>>> s.substitute(x='slurm')
"It's slurmtastic!"
>>> s = Template("Make $$ selling $x!")
>>> s.substitute(x='slurm')
'Make $ selling slurm!'
>>> s = Template('A $thing must never $action.')
>>> d = { 'thing': 'gentleman', 'action': 'show his socks'}
>>> s.substitute(d)
'A gentleman must never show his socks.'
```
