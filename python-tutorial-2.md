## Working with Strings  
All the standard sequence operations (indexing, slicing, multiplication, membership, length, minimum, and maximum) work with strings, however, strings are immutable. All kinds of item or slice assignments are illegal:  
```Python
>>> quote = 'To be or not be'
>>> quote[0:3]
'To '
>>> quote[0:3] = 2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
```
+ Formatting
The string formatting operator: the percent(%) sign. 
