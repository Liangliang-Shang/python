## Generator    
+ *```yield```*    
```Python
>>> def abcGenerator():
...     yield 'a'
...     yield 'b'
...     yield 'c'
...
>>> abcGenerator()
<generator object abcGenerator at 0xffdd13ec>
>>> for c in abcGenerator():
...     print c,
...
a b c
```
**Non-reusable Generator**  
```Python
>>> def countingDown(low, high):
...     while high >= low:
...             yield high
...             high -= 1
...
>>> g = countingDown(1, 10)
>>> g
<generator object countingDown at 0xffdd134c>
>>> for i in g:
...     print i,
...
10 9 8 7 6 5 4 3 2 1
>>> for i in g:
...     print i,
...
>>>
```
> If you don't want to load all the data in the memory, you can use a generator which will pass you each piece of data at a time. 
It is a good approach to work with lots of data to save the memory.    

**Infinite Generator**    
need *```break```* to get out of the infinite trap
```Python
>>> def infiniteGenerator(start=0):
...     while True:
...             yield start
...             start += 1
...
>>> for n in infiniteGenerator(10):
...     print n,
...     if n > 20:
...             break
...
10 11 12 13 14 15 16 17 18 19 20 21
```
**Reusable Generator**    
```Python
class Counter(object):
	def __init__(self, low, high):
		self.low	= low
		self.high	= high

	def __iter__(self):
		counter = self.low
		while self.high >= counter:
			yield counter
			counter += 1
```
```Python
>>> g = Counter(1, 9)
>>> for n in g:
...     print n,
...
1 2 3 4 5 6 7 8 9
>>> for n in g:
...     print n,
...
1 2 3 4 5 6 7 8 9
```
+ Generator Expression    
High performance, memory efficient generalization of list comprehensions and generators    
```Python
>>> l = [x * x for x in range(1, 10)]    # create a list of the square values in memory
>>> sum(l)
285
>>> g = (x * x for x in range(1, 10))    # a generator expression, save the memory usage
>>> g
<generator object <genexpr> at 0xffdd134c>
>>> sum(g)
285
```
