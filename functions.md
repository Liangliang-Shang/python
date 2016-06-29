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
def f(a, b):
    t = b / a + 1
    if b % a == 0: 
        return '1/%s' % (b / a)
    else: 
        return '1/%s + %s' % (t, f(a * t -b, b * t))
f(3, 7)
'1/3 + 1/11 + 1/231'
```
