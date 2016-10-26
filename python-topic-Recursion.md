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
### Fibnanci
```Python
>>> def fib(n):
...     if n in (0, 1):
...         return n
...     else:
...         return fib(n-1) + fib(n-2)
... 
>>> fib(0), fib(1), fib(2), fib(3), fib(4), fib(5), fib(6)
(0, 1, 1, 2, 3, 5, 8)
```
```python
#!/bin/env python
# -*- coding: UTF-8 -*-

'''
Tower of Hanoi
https://en.wikipedia.org/wiki/Tower_of_Hanoi
'''
import pprint

def hanoi(n, x, y, z, solution):
	if n == 1:
		action = (x, z)
		solution.append(action)
	else:
		hanoi(n-1, x, z, y, solution)
		action = (x, z)
		solution.append(action)
		hanoi(n-1, y, x, z, solution)

def initHanoi(n):
	l = range(1, n+1)
	l.reverse()

	solution = list()

	d = {
		'X': l
		, 'Y': list()
		, 'Z': list()
	}

	return solution, d

def move(src, dst): 
	dst.append(src.pop())

def display(d): 
	for key in sorted(d.keys()): 
		pprint.pprint(d[key]), 
	else: 
		print 

if __name__ == '__main__': 
	disks = raw_input('Please input the number of disks: ')
	solution, d = initHanoi(int(disks))
	x, y, z	= sorted(d.keys())
	
	hanoi(len(d['X']), x, y, z, solution)

	for (src, dst) in solution: 
		display(d)
		move(d[src], d[dst])
	else: 
		display(d)

```
