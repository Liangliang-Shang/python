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

+ String Methods  
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
>>> title = "Monty Python's Flying Circus"
>>> title.find('Monty')
0
>>> title.find('Python')
6
>>> title.find('Zirquss')
-1
>>> subject = '$$$ Get rich now!!! $$$'
>>> subject.find('$$$')
0
>>> subject.find('$$$', 1)
20
>>> subject.find('!!!')
16
>>> subject.find('!!!', 0, 16)
-1
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
>>> '*** SPAM * for * everyone!!! ***'.strip(' *!')
'SPAM * for * everyone'
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
