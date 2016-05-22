```Python
f = lambda s: False not in [ False if str(s)[i] != str(s)[-(i+1)] else True for i in range(len(str(s))/2) ]
f(1), f(11), f(121), f(12), f(123)
(True, True, True, False, False)
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
