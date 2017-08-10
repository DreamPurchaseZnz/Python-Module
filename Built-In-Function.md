Build-in-Functions(67)
--------------------------------------------------------------------------------------------------------		
```
# commenly used
abs                                                  ---> the absolute value
max                                                  ---> Return the largest item in an iterable
round                                                ---> Return the nearest integer to its input
min                                                  ---> Return the largest item in an iterable
len                                                  ---> The length of an object

open                                                 ---> Open a file and return a file object(file orient API)	
print                                                ---> Print object to text stream file  
format                                               ---> Convert  a value to a 'formatted' representation
list                                                 ---> Mutable squence type
range                                                ---> Specific number of times in for loops
zip                                                  ---> Return an iterator that aggregate elements from each of iteratles

isinstance                                           ---> Judge if the argument object is an instance of classinfo argument
type                                                 ---> The type of object
str

## other method
dict()	
help()	
setattr()
all()	
dir()	
hex()	
next()	
slice()
any()	
divmod()	
id()	
object()	
sorted()
ascii()	
enumerate()	
input()	
oct()	
staticmethod()
bin()	
eval()	
int()	
bool()	
exec()	
ord()	
sum() 
bytearray()	
filter()	
issubclass()	
pow()	
super()
bytes()	
float()	
iter()		
tuple()
callable()	
property()	
chr()	
frozenset()	
vars()
classmethod()	
getattr()	
locals()	
repr()	
compile()	  
globals()	
map()	
reversed()	
__import__()
complex()	
hasattr()	
delattr()	
hash()	
memoryview()	
set()
```
### open- write string to txt file
open() returns a file object, and is most commonly used with two arguments: open(filename, mode)

Methods
```
f.read
f.readline                    ---> Read a single line split by a newline character(\n)
f.write
f.writelines
f.tell            
f.seek(offset,fromwhat)       ---> Adding offset to a reference point
f.close
```

e.g.
```
f = open("path/name.txt", "w")
f.write("discription : %s" % variable)
f.close()
```
if you use a context manager ,the file is closed automatically for you
```
with open('path/name.text','w') as f:
   f.write('discription:{}'.format{variables})
```
Also we can write many lines at once.
```
with open('name.txt','w') as f:
    lines = ['line 1\n',
            'this is line 2\n'
            'this is line 3\n'
            'this is end']
    f.writelines(lines)

f = open('name.txt','r')
print(f.read())      
```

### format- present formatted value
Using % and .format() for great good! (reference)[https://pyformat.info/#named_placeholders]
```
Basic formatting
Value conversion
Padding and aligning strings
Truncating long strings
Combining truncating and padding
Numbers
Padding numbers

# specail arribute
Signed numbers
Named placeholders   
Getitem and Getattr
Datetime
Parametrized formats
Custom objects

```
e.g.

* Signed numbers
```
'{:=5d}'.format((- 23))

```

* Named placeholders
```
data = {'first': 'Hodor', 'last': 'Hodor!'}
'%(first)s %(last)s' % data
'{first} {last}'.format(**data)

'{first} {last}'.format(first='Hodor', last='Hodor!')
```

* Getitem and Getattr:
New style formatting allows even greater flexibility in accessing nested data structures.

```
person = {'first': 'Jean-Luc', 'last': 'Picard'}
'{p[first]} {p[last]}'.format(p=person)

data = [4, 8, 15, 16, 23, 42]
'{d[4]} {d[5]}'.format(d=data)

```
As well as accessing attributes on objects via getattr():
```
class Plant(object):
    type = 'tree'

'{p.type}'.format(p=Plant())
```

* Datetime
```
from datetime import datetime

'{:%Y-%m-%d %H:%M}'.format(datetime(2001, 2, 3, 4, 5))
```

* Parametrized formats
Parametrized formats are nested expressions in braces that can appear anywhere in the parent format after the colon
```
'{:{align}{width}}'.format('test', align='^', width='10')

# compare with %
'%*.*f' % (5, 2, 2.7182)
'{:{width}.{prec}f}'.format(2.7182, width=5, prec=2)
```
* Custom objects
```
class HAL9000(object):

    def __format__(self, format):
        if (format == 'open-the-pod-bay-doors'):
            return "I'm afraid I can't do that."
        return 'HAL 9000'
        
'{:open-the-pod-bay-doors}'.format(HAL9000())
```

