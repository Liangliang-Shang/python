## Closures    
```Python
>>> def f(x):
...     def g(y):
...         return x + y
...     return g
...
>>> f(0)
<function g at 0x000000000313A518>
>>> f(1)
<function g at 0x000000000313A828>
>>> f(0)(1)
1
>>> f(1)(9)
10
```

## Decorator    
