## String    
A string is a sequence of characters. All the standard sequence operations (indexing, slicing, multiplication, membership, length, minimum, and maximum) work with strings, however, strings are immutable. All kinds of item or slice assignments are illegal.    
+ Single-Quoted/Double-Quoted/Triple-Quoted Strings and Escaping Quotes    
```Python
>>> 'Hello, world!'                     # Single-Quoted string
'Hello, world!'
>>> 'Let\'s go!'                        # Back-slash to escapte the single quote in a single-quoted string
"Let's go!"
>>> "Let's go!"                         # The single quote could be used as a part of a Double-Quoted string
"Let's go!"
>>> '"Hello, world!" she said'          # vice-versa
'"Hello, world!" she said'
>>> '"Hello, world!" she said'
'"Hello, world!" she said'

# Triple-Quoted string for muliple-line strings, single/double quotes are freely used. 
>>> print '''This is a very long string. 
... It continues here. 
... And it's not over yet. 
... "Hello, world!"
... Still here.'''
This is a very long string. 
It continues here. 
And it's not over yet. 
"Hello, world!"
Still here.
>>> 
```
+ Immutable    
Once you create a string, you cannot change it anymore. 
```Python
>>> quote = 'To be or not be'
>>> quote[0:3]
'To '
>>> quote[0:3] = 2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
```
+ Escaping Sequences & Continuing lines    
  * \', \", \\, \t, \n
  * \    
    if \ is the last character of the line in python, which means the next line continues the last line.    

```Python
>>> print "Hello, \
... world!"
Hello, world!
>>> print \
...     'Hello, world!'
Hello, world!
>>> 1 + 2 + \
...     3 + 4
10
```  
+ Raw Strings  
Raw strings don't treat the backslash as a special character at all. The one thing you can't have in a raw string is a final backslash. It is very helpful when you are writing a Windows file system path or in a regular expression. 

```Python
>>> print 'Hello,\nworld!'
Hello,
world!
>>> print r'Hello,\nworld!'
Hello,\nworld!
>>> print r'Let\'s go!'
Let\'s go!
>>> print r"This is illegal\"
  File "<stdin>", line 1
    print r"This is illegal\"
                            ^
SyntaxError: EOL while scanning string literal
>>> print r"C:\Program Files" '\\'               # to avoid double back slash to escapte \
C:\Program Files\
>>> 
```
+ Unicode Strings  
Normal strings in Python are stored internally as 8-bit ASCII, while Unicode strings are stored as 16-bit Unicode. This allows for a more varied set of characters, including special characters from most languages in the world.    

```Python
>>> print u'你好！'
你好！
```
### String Representations, str and repr    
_str_ simply converts a value into a string in some reasonable fashion that will probably be understood by a user, and _repr_, which creates a string that is representation of the value as a legal Python expression.    

```Python
>>> "Hello, world!"
'Hello, world!'
>>> 10000L
10000L
>>> print "Hello, world!"
Hello, world!
>>> print 10000L
10000
>>> print repr("Hello, world!")
'Hello, world!'
>>> print repr(10000L)
10000L
```

### Concatenate Strings    

```Python
>>> "Let's say " '"Hello, world!"'
'Let\'s say "Hello, world!"'
>>> "Hello, " + "world!"
'Hello, world!'
```

### Format    
str.format method is much more simpler and eligant than string concatenation, and  the conversion to string would be done automatically
```python
# format string
print '{}, {}'.format('abc', 'xyz')                # position matters
print '{}, {}'.format('xyz', 'abc')                # position matters
print '{0}, {1}, {0}'.format('abc', 'xyz')         # position reusable
```

    abc, xyz
    xyz, abc
    abc, xyz, abc
    


```python
# format string (continued)
print '{first}, {last}'.format(last='abc', first='xyz')             # keyword parameters
print '{first}, {last}, {first}'.format(last='abc', first='xyz')    # keyword reusable
```

    xyz, abc
    xyz, abc, xyz
    


```python
# format string (continued)
import this
print '{self.i}{self.c}'.format(self=this)          # class/object/module
```

    25!
    


```python
# format string (continued)
l = ('a', 'b', 'c')
print '{0[2]}-{0[1]}-{0[0]}'.format(l)              # format a list
d = {'a': 'x', 'b': 'y', 'c': 'z'}
print '{0[a]},{0[b]},{0[c]}'.format(d)              # format a dict
```

    c-b-a
    x,y,z
    


```python
# format numbers/with style? 
pi = 3.1415926
print '{:0<9}'.format('{:.2f}'.format(pi))
x  = 23
print '{0:0<17} = {1:0>17}'.format(pi, pi)               # position:padding{align:^|<|>}length
d  = 127
print '{0:d}(d) = {0:b}b = {0:o}o = {0:x}x'.format(d)    # decimal, binary, oct, hex
print '{0:0<17} = {0:,}'.format(pi * 1000000)            # 314,159.26
```

    3.1400000
    3.141592600000000 = 000000003.1415926
    127(d) = 1111111b = 177o = 7fx
    3141592.600000000 = 3,141,592.6

```Python
>>> print('{0}{1: ^72}{0}'.format('+', 'README'))         # fill with ' ' with the text centered in 72 width
+                                 README                                 +
```

+ Formatting  
The string formatting operator: the percent(%) sign. 
```Python
>>> format = "Hello, %s. %s enough for ya?"
>>> values = ('world', 'Hot')
>>> print format % values
Hello, world. Hot enough for ya?
>>> from math import pi
>>> print format % pi
Pi with three decimals: 3.142
```
  + TEMPLATE STRINGS
```Python
>>> from string import Template
>>> s = Template('$x, glorious $x!')
>>> s.substitute(x='slurm')
'slurm, glorious slurm!'
>>> s = Template("It's ${x}tastic!")
>>> s.substitute(x='slurm')
"It's slurmtastic!"
>>> s = Template("Make $$ selling $x!")
>>> s.substitute(x='slurm')
'Make $ selling slurm!'
>>> s = Template('A $thing must never $action.')
>>> d = { 'thing': 'gentleman', 'action': 'show his socks'}
>>> s.substitute(d)
'A gentleman must never show his socks.'
```

+ More about formatting  
  The order:  
  + **The % character.** This marks the beginning of the conversion specifier.
  + **Conversion flags (optional).** These may be either -, indicating left alignment; +, indicating that a sign should precede the converted value; “ ” (a space character), indicating that a space should precede positive numbers; or 0, indicating that the conversion should be zero-padded.
  + **The minimum field width (optional).** The converted string will be at least this wide. If this is an * (asterisk), the width will be read from the value tuple.
  + **A . (dot) followed by the precision (optional).** If a real number is converted, this many decimals should be shown. If a string is converted, this number is that maximum field width. If this is an * (asterisk), the precision will be read from the value tuple.
  + **The conversion type.**  
    **d, i**                Signed integer decimal  
    **o**                   Unsigned octal  
    **u**                   Unsigned decimal  
    **x**                   Unsigned hexadecimal (lowercase)  
    **X**                   Unsigned hexadecimal (uppercase)  
    **e**                   Floating point exponential format (lowercase)  
    **E**                   Floating point exponential format (uppercase)  
    **f, F**                Floating point decimal format  
    **g**                   Same as e if exponent is greater than –4 or less than precision, f otherwise  
    **G**                   Same as E if exponent is greater than –4 or less than precision, F otherwise  
    **c**                   Single character (accepts integer or single character string)  
    **r**                   String (converts any Python object using repr)  

```Python
>>> pi = math.pi
>>> pi
3.141592653589793
>>> '%10f' % pi
'  3.141593'
>>> '%10.2f' % pi
'      3.14'
>>> '%.2f' % pi
'3.14'
>>> '%.5s' % 'Guido van Rossum'
'Guido'
>>> '%.*s' % (5, 'Guido van Rossum')
'Guido'
```
  + Signs, Alignment, and Zero-Padding
```Python
>>> print ('% 5d' % 10) + '\n' + ('% 5d' % -10)
   10
  -10
>>> print ('%+5d' % 10) + '\n' + ('%+5d' % -10)
  +10
  -10
```

### String Methods  
  + string.digits
  + string.letters
  + string.lowercase
  + string.printable
  + string.punctuation
  + string.uppercase
  + find/rfind/index/rindex/count/startswith/endswith
  + join
  + lower/translate/islower/capitalize/swapcase/title/istitle/upper/isupper
  + replace/translate/expandtabs
  + split/rsplit/splitlines
  + strip/lstrip/rstrip
  + translate
```Python
>>> import string
>>> string.digits
'0123456789'
>>> string.letters
'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
>>> string.lowercase
'abcdefghijklmnopqrstuvwxyz'
>>> string.printable
'0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~ \t\n\r\x0b\x0c'
>>> string.punctuation
'!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~'
>>> string.uppercase
'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
```
** Find a sub-string
```Python
>>> zen = 'Now is better than never.\n'
>>> zen.find('er')                         # find 'er' from 0
11
>>> zen.find('er', zen.find('er')+1)       # find 'er' after the first 'er', actually find the second 'er'
22
>>> zen.find('er', 0, 9)                   # find 'er' between 0 and 9
-1
>>> zen.find('is', 0, 9)
4
>>> zen.find('wisdom')                     # cannot find the sub-string, return -1
-1
>>> zen.rfind('er')                        # find 'er' starting from the right side, return its index
22
>>> zen.index('wisdom')                    # str.index method throws ValueError, except that, no different from find?
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: substring not found
>>> zen.count('n')
2
>>> zen.startswith('Now')
True
>>> zen.endswith('never')
False
```
```
>>> seq = [1, 2, 3, 4, 5]
>>> sep = '+'
>>> sep.join(seq)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: sequence item 0: expected string, int found
>>> sep.join([str(i) for i in seq])
'1+2+3+4+5'
>>> 'ABC'.lower()
'abc'
>>> '''let's go'''.replace("'s", ' us')
'let us go'
>>> '1+2+3+4+5'.split('+')
['1', '2', '3', '4', '5']
```
** Strip characters from a string **
```Python
>>> '*** SPAM * for * everyone!!! ***'.strip(' *!')
'SPAM * for * everyone'
>>> '*** SPAM * for * everyone!!! ***'.lstrip('*')
' SPAM * for * everyone!!! ***'
>>> '*** SPAM * for * everyone!!! ***'.rstrip('*')
'*** SPAM * for * everyone!!! '
>>> '*** SPAM * for * everyone!!! ***'.lstrip('*').strip()      # strip() default strip leading/trailing white spaces 
'SPAM * for * everyone!!! ***'
```
```
>>> from string import maketrans
>>> table = maketrans(string.lowercase, string.uppercase)
>>> 'abc'.translate(table)
'ABC'
>>> len(table)
256
>>> table[97:123]
'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
>>> maketrans('', '')[97:123]
'abcdefghijklmnopqrstuvwxyz'
```
+ Tricks
```Python
>>> s1, s2 = 'abc', 'aba'
>>> s1 == s1[::-1], s2 == s2[::-1]
(False, True)
```
