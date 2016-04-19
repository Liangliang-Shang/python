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
>>> print greeting, salutation, name 
Hello, Mr. Gumby # combine text and variable values without using the full power of string formatting
>>> greeting = 'Hello'                        # greeting had no comma
>>> print greeting, ',', salutation, name     # add ','
Hello , Mr. Gumby                             # introduce a space before the comma
>>> print greeting + ',', salutation, name
Hello, Mr. Gumby
print 'Hello,',   # add a comma at the end, the next print statement will continue printing on the same line
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
```Python
>>> x = y = [1, 2, 3]     # the variables x and y have been bound to the same list
>>> z = [1, 2, 3]         # z is simply bound to another list that happens to contain the same values in the same order.
>>> id(x)
140676740418448
>>> id(y)
140676740418448
>>> id(z)
140676740418376
>>> x == y        # check if x and y are equal
True
>>> x == z
True
>>> x is y        # check if x and y are the same object based on identity, rather than equality
True
>>> x is z
False
>>> y is z
False
```
```Python
>>> number = 6
>>> 1<= number <= 10    # chained comparison
True
```
### Assertions  
```Python
>>> age = 10
>>> assert 0 < age < 100
>>> age = -1
>>> assert 0 < age < 100                                    # it is useful as a checkpoint
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError
>>> assert 0 < age < 100, 'The age must be realistic'       # to explain the assertion
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError: The age must be realistic
```
### while 
```Python
>>> x = 0
>>> while x <= 3:
...     print x
...     x += 1
... 
0
1
2
3
>>> name = ''
>>> while not name:
...     name = raw_input('Please enter your name: ')
... 
Please enter your name: 
Please enter your name: 
Please enter your name:       # keep asking for entering an un-empty string as name
```
### for loops
```Python
>>> numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> for number in numbers:
...     print number
... 
0
1
2
3
4
5
6
7
8
9
>>> range(10)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> range(0, 10)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> d = {'x': 1, 'y': 2, 'z': 3}
>>> for key in d: 
...     print key, 'corresponds to', d[key]
... 
y corresponds to 2
x corresponds to 1
z corresponds to 3
>>> for key, value in d.items():
...     print key, 'corresponds to', value
... 
y corresponds to 2
x corresponds to 1
z corresponds to 3
>>> for k in d.iterkeys():        # more efficient
...     print k
... 
y
x
z
>>> for v in d.itervalues():
...     print v
... 
2
1
3
>>> for k, v in d.iteritems():
...     print k, v
... 
y 2
x 1
z 3
```
```Python
>>> names = ['anne', 'beth', 'george', 'damon']
>>> ages = [12, 45, 32, 102]
>>> zip(names, ages)
[('anne', 12), ('beth', 45), ('george', 32), ('damon', 102)]
>>> for name, age in zip(names, ages):
...     print name, 'is', age, 'years old'
... 
anne is 12 years old
beth is 45 years old
george is 32 years old
damon is 102 years old
>>> for index, name in enumerate(names):
...     print index, name
... 
0 anne
1 beth
2 george
3 damon
>>> zip(range(5), xrange(1000000000000000000))    # it stops when the shortest sequence is "used up"
[(0, 0), (1, 1), (2, 2), (3, 3), (4, 4)]          # using xrange instead of range
```
### Breaking out of loops  
+ break  
+ continue  
+ else  

### List Comprehension
```Python
>>> [ x*x for x in range(10)]
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>>> [ x*x for x in range(10) if x % 3 == 0]
[0, 9, 36, 81]
>>> [ (x,y) for x in range(4) if x % 3 == 0 for y in range(3) if y % 2 ==0]
[(0, 0), (0, 2), (3, 0), (3, 2)]
```

### pass/del/exec
```Python
>>> pass          # nothing going here / nothing happened! could be a placeholder, or could define a string 
>>> 
```
```Python
>>> x = ["Hello", "world"]
>>> y = x                     # x and y are refering to the same list 
>>> id(x)
140676739873320
>>> id(y)
140676739873320
>>> y[1] = "Python"
>>> x
['Hello', 'Python']
>>> y
['Hello', 'Python']
>>> del x                     # only delete the name x bound to the list, not the list itself(the value)
>>> y                         # through y, we could access to the list
['Hello', 'Python']
>>> del y                     # the list floats around in the memory of the computer with no name attached to it. 
# No way to retrieve the list or use it. GC will deletes it. No way to delete values or even no need to do that. 
```
```Python
>>> exec "print 'Hello, world!'"
Hello, world!
>>> from math import sqrt
>>> scope = {}                      # a namespace as a place where you keep your variables. 
>>> exec 'sqrt = 1' in scope        # without overwritten the sqrt function
>>> sqrt(4)
2.0
>>> scope['sqrt']
1
```
```Python
>>> eval(raw_input("Enter an arithmetic expression: "))     # is equivalent to input(...)
Enter an arithmetic expression: 6 + 18 * 2
42
>>> scope = {}          
>>> scope['x'] = 2
>>> scope['y'] = 3
>>> eval('x*y', scope)      # evaluates a Python expression (written in a string) and returns the value
6
>>> exec('x=x*x', scope)    # executes a series of Python statements without returning any thing
>>> scope['x']
4
```
