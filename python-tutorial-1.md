
*A data structure is a collection of data elements (such as numbers or characters -- or even other data structures) that is structured in some way, for example, by numbering the elements.*  

*Python has six built-in types of sequences: lists, tuples, strings, Unicode strings, buffer objects, xranges objects.*  

## Sequences  
A sequence is a data structure in which the elements are numbered (starting with zero). Examples of sequence types are lists, strings, and tuples. Of these, lists are mutable, whereas tuples and strings are immutable. 
```Python
>>> edward = ['Edward Gumby', 42]
>>> john   = ['John Smith', 50]
>>> database = [edward, john]
>>> database
[['Edward Gumby', 42], ['John Smith', 50]]
```
### Common Sequence Operations
+ Indexing  
All elements in a sequence are numbered - from zero and upwards.  
_A string is just a sequence of characters._  
When you use a negative index, Python counts from the right, that is, from the last element. The last element is at position -1 (not -0, as that would be the same as the first element): 
```Python
>>> greeting = 'Hello'
>>> greeting[0]
'H'
>>> greeting[-1]                               # a negative index, counting from the right, the last element.
'o'
>>> 'Hello'[1]
'e'
>>> third = raw_input('Year: ')[2]
Year: 2016
>>> third
'1'
```
+ Slicing  
Slicing to access ranges of elements by using two indices, separated by a colon.
```Python
>>> numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> numbers[3:6]                              # the first is inclusive, and the second is exclusive
[4, 5, 6]
>>> numbers[7:20]
[8, 9, 0]
>>> numbers[-3:-1]                            # counting from the right, excluding the last one
[8, 9]
>>> numbers[-3:0]                             # return an empty list
[]
>>> numbers[-3:]                              # the last three elements
[8, 9, 0]
>>> numbers[:3]                               # the first three elements
[1, 2, 3]
>>> numbers[:]                                # copy the entire sequence
[1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> numbers[0:10:2]                           # step = 2
[1, 3, 5, 7, 9]
>>> numbers[::4]                              # step = 4
[1, 5, 9]
>>> numbers[10:0:-2]                          # counting from the right, step = 2
[0, 8, 6, 4, 2]
>>> numbers[5::-2]
[6, 4, 2]
>>> numbers[:5:-2]
[0, 8]
>>>
```
+ Adding Sequences
** In general, you can only concatenate two sequences of the same kind. **
```Python
>>> [1, 2, 3] + [4, 5, 6]
[1, 2, 3, 4, 5, 6]
>>> 'Hello, ' + 'world!'
'Hello, world!'
>>> [1, 2, 3] + 'world!'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate list (not "str") to list
>>> 
```
+ Multiplication  
Multiplying a sequence by a number x creates a new sequence where the original sequence is repeated x times: 
```Python
>>> 'Abc' * 3
'AbcAbcAbc'
>>> [1, 2, 3] * 5
[1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3]
```
+ None, Empty Lists, and Initialization
```Python
>>> emptyList = []
>>> sequence = [None] * 10                     # init a list of length 10, with None, meaning "nothing here"
>>> emptyList
[]
>>> sequence
[None, None, None, None, None, None, None, None, None, None]
```
+ Membership  
```Python
>>> numbers
[1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> 1 in numbers
True
>>> 10 in numbers
False
>>> 'P' in 'Python'
True
```
+ Length, Minimum, and Maximum
```Python
>>> numbers
[1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> len(numbers)
10
>>> min(numbers)
0
>>> max(numbers)
9
```

## List
+ The list Function    
Create a list from a string
```Python
>>> list('Hello')                 # ''.join(['H', 'e', 'l', 'l', 'o']) 
['H', 'e', 'l', 'l', 'o']
```

### Copy of a list
```Python
>>> x = [4, 6, 2, 1, 7, 9]

>>> y = x                          # x/y are binding to the same object. 
>>> y is x
True
>>> id(x), id(y)
(4292289772L, 4292289772L)

>>> y = x[:]                       # two different objects, the one y binds copy the value of x
>>> y is x
False
>>> id(x), id(y)
(4292289772L, 4292730412L)
```

### Basic List Operations  
  + Item Assignments  
  + Deleting Elements  
  + Assigning to Slices  
    Replace/Extend/Insert/Delete...
```Python
>>> x = [1, 1, 1]
>>> x[1] = 2
>>> x
[1, 2, 1]
>>> x[9] = 10                    # None to initialize the list, then assign value to it. x = [None] * 10???
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list assignment index out of range
```
```Python
>>> x
[1, 2, 1]
>>> del x[0]
>>> x
[2, 1]
```
```Python
>>> name = list('Perl')
>>> name
['P', 'e', 'r', 'l']
>>> name[2:] = list('ar')
>>> name
['P', 'e', 'a', 'r']
>>> name[1:] = list('ython')
>>> name
['P', 'y', 't', 'h', 'o', 'n']
>>> numbers = [1, 5]
>>> numbers[1:1] = [2, 3, 4]                    # worked as insert
>>> numbers
[1, 2, 3, 4, 5]
>>> numbers[2:] = []                            # worked as delete, del numbers[1:4]
>>> numbers
[1, 2]
```
### Methods    

  + **list.copy()**    
  Return a shallow copy of the list.    
  + **list.count(x)**    
  Return the number of times x appears in the list.
  + **list.index(x)**    
  Return the index in the list of the first item whose value is x. It is an error if there is no such item.    

  + **list.append(x)**    
  Add an item to the end of the list
  + **list.extend(l)**    
  Extend the list by appending all the items in the given list. 
  + **list.insert(i, x)**    
  Insert an item at a given position. 
  + **list.pop(i)**    
  Remove the item at the given position in the list, and return it. If no index is specified, a.pop() removes and returns the last item in the list.
  + **list.remove(x)**    
  Remove the first item from the list whose value is x. It is an error if there is no such item.    
  + **list.reverse()**    
  Reverse the elements of the list in place.
  + **list.sort(key=None, reverse=False)**    
  Sort the items of the list in place
  + **list.clear()**    
  Remove all items from the list.    

**Count/Index**
```Python
>>> q = ['to', 'be', 'or', 'not', 'to', 'be']
>>> q.copy()                                        # Equivalent to q[:]
['to', 'be', 'or', 'not', 'to', 'be']
>>> q.count('to')
2
>>> q.count('is')                                   # No 'is' in the list
0
>>> q.index('not')
3
>>> q.index('is')                                   # ValueError!!!
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: 'is' is not in list
```

**Change the list**    
```Python
>>> numbers = range(1, 9)
>>> numbers
[1, 2, 3, 4, 5, 6, 7, 8]
>>> numbers.append(9)                    # Equivalent to numbers[len(numbers):] = 9
>>> numbers
[1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> numbers.extend(numbers[0:3])         # Equivalent to numbers[len(numbers):] = numbers[0:3]
>>> numbers                              #  numbers + numbers[0:3]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 1, 2, 3]
>>> numbers.insert(0, 0)                 # Equivalent to numbers[0:0] = (0, )
>>> numbers
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 1, 2, 3]
>>> numbers.remove(3)                    # Remove the first concurreny 3
>>> numbers
[0, 1, 2, 4, 5, 6, 7, 8, 9, 1, 2, 3]
>>> numbers.pop(4)                       # pop out the element at the index 4, and return the value 5
5
>>> numbers.reverse()                    # reverse the list. how about list(reversed(numbers))???
>>> numbers
[3, 2, 1, 9, 8, 7, 6, 4, 2, 1, 0]
>>> numbers.sort()                       # sort the list. sort(reverse=True)!!! how about sorted(numbers)???
>>> numbers
[0, 1, 1, 2, 2, 3, 4, 6, 7, 8, 9]
>>> x = ['a', 'another', 'about', 'an']  # sort by the key specified by the argument key
>>> x.sort(key=len)
>>> x
['a', 'an', 'about', 'another']
>>> x.clear()                            # Remove all the elements and then become an empty list
>>> x
[]
```
More about sort. 
```Python
>>> cmp(42, 32)
1
>>> cmp(99, 100)
-1
>>> cmp(10, 10)
0
>>> numbers = [5, 2, 9, 7]
>>> numbers.sort(cmp)
>>> numbers
[2, 5, 7, 9]
```

### Simulate Stack/Queue
+ Use *list.pop()*/*list.append()* to simulate Stack, LIFO(Last In First Out)
+ Use *list.pop(0)*/*list.append()* to simulate Queue, FIFO(First In First Out)
```Python
>>> a = range(0, 5)
>>> a.pop()                 # pop out the last member, 4
4
>>> a.pop()                 # pop out the last member, now it is 3
3
>>> a
[0, 1, 2]
>>> a.append(3)             # append 3 to the list tail
>>> a
[0, 1, 2, 3]
```
```Python
>>> a = range(5)
>>> a.append(1)             # into the queue
>>> a.pop(0)                # out of the queue (inserting or poping from the begining is going to shift all of the other elements)
0
>>> a.pop(0)                # out of the queue
1
>>> a
[2, 3, 4, 1]
```
To implement a queue, use collections.deque    
```Python
>>> from collections import deque
>>> queue = deque(list(range(5)))
>>> queue
deque([0, 1, 2, 3, 4])
>>> queue.append(5)
>>> queue.append(5)
>>> queue.popleft()
0
>>> queue.popleft()
1
>>> queue
deque([2, 3, 4, 5, 5])
```

## Tuples: Immutable Sequences
```Python
>>> 1, 2, 3                  # a tuple
(1, 2, 3)
>>> (1, 2, 3)                # a tuple 
(1, 2, 3)
>>> ()                       # an empty tuple
()
>>> 42                       # just an integer
42
>>> 42,                      # a tuple with one element
(42,)
>>> (42,)                    # a tuple with one element
(42,)
>>> 3 * (42)                 # equal to 3 * 42
126
>>> 3 * (42, )               # elements repeats three times in a tuple
(42, 42, 42)
```
**The comma is crucial for a tuple. Simply adding parentheses won't help: (42) is exactly the same as 42.**
+ the tuple function
+ Basic Tuple Operations
  + Make tuples  
  + Access their elements  
  slices of a tuple are also tuples. 
```Python
>>> tuple([1, 2, 3])
(1, 2, 3)
>>> tuple('abc')
('a', 'b', 'c')
>>> tuple((1, 2, 3))
(1, 2, 3)
>>> a = (1, 2, 3, 4)
>>> del a[0]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object doesn't support item deletion
>>> x, y = divmod(15, 2)          # divmod return a tuple (quotient, remainder), and unpack it with x, y
>>> x, y
(7, 1)
```
**Tuples are immutable, that means you can not del/add/edit any value inside the tuple.**
