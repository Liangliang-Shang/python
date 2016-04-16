## More about print and import
```Python
>>> print 'Age:', 42    # print an expression, which is either a string or is automatically converted to one. 
Age: 42                 # A space character is inserted between each argument. 
>>> 1, 2, 3             # form a tuple
(1, 2, 3)
>>> print 1, 2, 3       # the arguments of print do not form a tuple
1 2 3
>>> print (1, 2, 3)
(1, 2, 3)
>>> name = 'Gumby'
>>> salutation = 'Mr.'
>>> greeting = 'Hello,'
>>> print greeting, salutation, name    # combine text and variable values without using the full power of string formatting
Hello, Mr. Gumby
>>> greeting = 'Hello'                        # greeting had no comma
>>> print greeting, ',', salutation, name     # add ','
Hello , Mr. Gumby                             # introduce a space before the comma
>>> print greeting + ',', salutation, name
Hello, Mr. Gumby
print 'Hello,',         # add a comma at the end, the next print statement will continue printing on the same line
print 'world!'
Hello, world!  
```
## Importing Something As Something Else
import somemodule

from somemodule import somefunction

from somemodule import *

## Sequence Unpacking
```Python
>>> x, y, z = 1, 2, 3
>>> print x, y, z
1 2 3
>>> x, y = y, x
>>> print x, y, z
2 1 3
>>> values = 1, 2, 3
>>> values
(1, 2, 3)
>>> x, y, z = values    # unpack a sequence of variables 
>>> x
1
>>> scoundrel = {'name': 'Robin', 'girlfriend': 'Marion'}
>>> key, value = scoundrel.popitem()      # pop out one item of key-value pair
>>> key
'girlfriend'
>>> value
'Marion'
```
> In general, you should not use += with strings, especially if you are building a large string piece by piece in a loop.  
> Each addition and assignment needs to create a new string, and that takes time, making your program slower.  
> A much better approach is to append the small strings to a list,  
> and use the string method join to create the big string when your list is finished.  

## Block & Indentation  
A block is a group of statements that can be executed if a condition is true (conditional statements),    
or executed several times (loops), and so on. A block is created by indenting a part of your code; that is,    
putting spaces in front of it.  

### Conditions and Conditional Statements  
> False Values:    
> False    None    0    ""    ()    []    {}
```Python
>>> True
True
>>> False
False
>>> True == 1
True
>>> False == 0
True
>>> True + False + 42
43
>>> bool('I think, therefore I am')
True
>>> bool(42)
True
>>> bool('')
False
>>> bool(0)
False
```
### Conditional Execution and the if Statement
```Python
>>> num = input('Enter a number: ')
Enter a number: 6
>>> if num > 0:
...     print 'The number is positive'
... elif num < 0:
...     print 'The number is negative'
... else: 
...     print 'The number is zero'
... 
The number is positive
```
