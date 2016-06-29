```Python
f = lambda s: False not in [ False if str(s)[i] != str(s)[-(i+1)] else True for i in range(len(str(s))/2) ]
f(1), f(11), f(121), f(12), f(123)
(True, True, True, False, False)
```

```Python
f = lambda s: sum( str(s).count(e) for e in str(s) ) == len(str(s))
f(1), f(11), f(12), f(101), f(102), f('a'), f('ab'), f('too')
(True, False, True, False, True, True, True, False)
```

```python
def commonFactorial(n=0):
    '''
    commonFactorial(n=0) -> int
    
    calculate n! = 1*2*...*n
    '''
    result = 1
    for x in xrange(1, n): 
        result = result * (x+1)
    else: 
        return result

def recursiveFactorial(n=0):
    '''
    recursiveFactorial(n=0) -> int
    
    calculate n! = n*(n-1)!
    '''
    if n <= 1: 
        return 1
    else: 
        return n * recursiveFactorial(n-1)
        
(commonFactorial(), commonFactorial(-1), commonFactorial(0), commonFactorial(5), 
recursiveFactorial(), recursiveFactorial(-1), recursiveFactorial(0), recursiveFactorial(5))    

(1, 1, 1, 120, 1, 1, 1, 120)    
```
```Python
def recursiveFib(n=0):
    '''
    recursiveFib(n=0) -> int
    
    calculate fib number fib(n) = fib(n-1) + fib(n-2)
    '''
    if n in (1, 2):
        return 1
    else: 
        return fib(n-1) + fib(n-2)

def sequentialFib(n=0):
    '''
    sequentialFib(n=0) -> int
    
    calculate fib number sequentially, 
    init a list l = [1, 1], l.append(l[1] + l[0]) ( actually l[2] = 1 + 1 )
    and so on quentially calculate fib numbers
    return the list [n-1]
    '''
    l = [1, 1]
    
    for x in xrange(n):
        if x in (0, 1): 
            continue
        else:
            l.append(l[x-1] + l[x-2])
    else: 
        return l[n-1]
    
(recursiveFib(1), recursiveFib(2), recursiveFib(3), recursiveFib(4), recursiveFib(5), 
 sequentialFib(1), sequentialFib(2), sequentialFib(3), sequentialFib(4), sequentialFib(5))

(1, 1, 2, 3, 5, 1, 1, 2, 3, 5)
```

```Python
def f(a, b):
    t = b / a + 1
    if b % a == 0: 
        return '1/%s' % (b / a)
    else: 
        return '1/%s + %s' % (t, f(a * t -b, b * t))
f(3, 7)
'1/3 + 1/11 + 1/231'
```
