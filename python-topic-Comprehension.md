## Comprehension    

```python
# comprehension
print [ x for x in range(10) if x % 2 ]              # list comprehension, get a list
print { x for x in range(10) if x % 2 }              # set comprehension, get a set ( {} defines a set)
print { int(x/2): x for x in range(10) if x % 2 }    # dict comprehension, get a dict
print ( x for x in range(10) if x % 2)               # a generator object, O(1)
for i in (x for x in range(10) if x % 2):       
    print i, 
```

    [1, 3, 5, 7, 9]
    set([1, 3, 9, 5, 7])
    {0: 1, 1: 3, 2: 5, 3: 7, 4: 9}
    <generator object <genexpr> at 0x000000000409E708>
    1 3 5 7 9
