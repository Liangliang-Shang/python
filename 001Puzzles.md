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
