
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
+ Indexing  
All elements in a sequence are numbered - from zero and upwards.  
_A string is just a sequence of characters._  
When you use a negative index, Python counts from the right, that is, from the last element. The last element is at position -1 (not -0, as that would be the same as the first element): 
```Python
>>> greeting = 'Hello'
>>> greeting[0]
'H'
>>> greeting[-1]
'o'
>>> 'Hello'[1]
'e'
>>> third = raw_input('Year: ')[2]
Year: 2016
>>> third
'1'
```
+ Slicing  
Slicing to access ranges of elements
```Python
>>> numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> numbers[3:6]
[4, 5, 6]
>>> numbers[7:20]
[8, 9, 0]
>>> numbers[-3:-1]
[8, 9]
>>> numbers[-3:0]
[]
>>> numbers[-3:]
[8, 9, 0]
>>> numbers[:3]
[1, 2, 3]
>>> numbers[:]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> numbers[0:10:2]
[1, 3, 5, 7, 9]
>>> numbers[::4]
[1, 5, 9]
>>> numbers[10:0:-2]
[0, 8, 6, 4, 2]
>>> numbers[5::-2]
[6, 4, 2]
>>> numbers[:5:-2]
[0, 8]
>>>
```
+ Adding Sequences
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
>>> sequence = [None] * 10
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

## Lists
+ The list Function
Create a list from a string
```Python
>>> list('Hello')
['H', 'e', 'l', 'l', 'o']
```
+ Basic List Operations  
  + Changing Lists: Item Assignments  
  + Deleting Elements  
  + Assigning to Slices  
    Replace/Extend/Insert/Delete...
```Python
>>> x = [1, 1, 1]
>>> x[1] = 2
>>> x
[1, 2, 1]
>>> x[9] = 10
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
>>>
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
>>> numbers[1:1] = [2, 3, 4]
>>> numbers
[1, 2, 3, 4, 5]
>>> numbers[2:] = []
>>> numbers
[1, 2]
```
+ List Methods
  + append
  + count
  + extend
  + index
  + insert
  + pop
  + remove
  + reverse
  + sort
```Python
>>> lst = [1, 2, 3]
>>> lst.append(4)
>>> lst
[1, 2, 3, 4]
>>> ['to', 'be', 'or', 'not', 'to', 'be'].count('to')
2
>>> x = [[1, 2], 1, 1, [2, 1, [1, 2]]]
>>> x.count(1)
2
>>> x.count([1, 2])
1
```
Check out the difference betwen extending a list and concatenating it. 
```Python
>>> a = [1, 2, 3]
>>> b = [4, 5, 6]
>>> a.extend(b)
>>> a
[1, 2, 3, 4, 5, 6]
>>> a = [1, 2, 3]
>>> b = [4, 5, 6]
>>> a + b
[1, 2, 3, 4, 5, 6]
>>> a
[1, 2, 3]
>>> a[len(a):] = b
>>> a
[1, 2, 3, 4, 5, 6]
```
```Python
>>> a
[1, 2, 3, 4, 5, 6]
>>> a.index(3)
2
>>> a.index(0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: 0 is not in list
>>> numbers = [1, 2, 3, 5, 6, 7]
>>> numbers.insert(3, 'four')
>>> numbers
[1, 2, 3, 'four', 5, 6, 7]
>>> numbers = [1, 2, 3, 5, 6, 7]
>>> numbers[3:3] = ['four']
>>> numbers
[1, 2, 3, 'four', 5, 6, 7]
>>> numbers
[1, 2, 3, 'four', 5, 6, 7]
>>> numbers.pop()
7
>>> numbers
[1, 2, 3, 'four', 5, 6]
>>> numbers.pop(0)
1
>>> numbers
[2, 3, 'four', 5, 6]
>>> numbers.remove('four')
>>> numbers
[2, 3, 5, 6]
>>> numbers.remove(0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: list.remove(x): x not in list
>>> numbers
[2, 3, 5, 6]
>>> numbers.reverse()
>>> numbers
[6, 5, 3, 2]
>>> x = [1, 2, 3]
>>> list(reversed(x))
[3, 2, 1]
>>> x
[1, 2, 3]
>>> x = [4, 6, 2, 1, 7, 9]
>>> x.sort()
>>> x
[1, 2, 4, 6, 7, 9]
>>> x = [4, 6, 2, 1, 7, 9]
>>> y = x[:]
>>> y.sort()
>>> x
[4, 6, 2, 1, 7, 9]
>>> y
[1, 2, 4, 6, 7, 9]
>>> x
[4, 6, 2, 1, 7, 9]
>>> y = x
>>> y.sort()
>>> x
[1, 2, 4, 6, 7, 9]
>>> y
[1, 2, 4, 6, 7, 9]
x = [4, 6, 2, 1, 7, 9]
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
>>> x = ['a', 'another', 'about', 'an']
>>> x.sort(key=len)
>>> x
['a', 'an', 'about', 'another']
>>> x = [4, 6, 2, 1, 7, 9]
>>> x.sort(reverse=True)
>>> x
[9, 7, 6, 4, 2, 1]
```

## Tuples: Immutable Sequences
```Python
>>> 1, 2, 3
(1, 2, 3)
>>> (1, 2, 3)
(1, 2, 3)
>>> ()
()
>>> 42
42
>>> 42, 
(42,)
>>> (42,)
(42,)
>>> 3 * (42)
126
>>> 3 * (42, )
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
```
