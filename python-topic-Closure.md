## Closures    
Functions are also objects in Python, just like everything else. That means you can pass functions to functions as arguments or return functions from functions as return values. 
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
A decorator is nothing else but a function that returns a functions. 
