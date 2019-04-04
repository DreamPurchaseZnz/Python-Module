# Struct
Interpret strings as packed binary data

This module perform conversions between python values and C structs represented as python strings

## Functions and exceptions
```
struct.pack(fmt, v1, v2, ...)                     # pack v1,... according to the given fmt.
struct.packinto(fmt, buffer, offset, v1, v2,..)   # write packed bytes into a buffer starting at offset
struct.unpack(fmt, string)                        # unpack accoring to the fmt
struct.unpack(fmt, buffer[, offset=0])            # unpack the buffer
struct.calcsize(fmt)

```
## format strings
format strings are the mechanism used to specify the expected layout

the first character of the format string 
can be used to indicate the byte order, size and alignment of the packed data, according to the following table:
```

Character            Byte order	                 Size   	 Alignment
@	                   native                      native	    native
=                    native             	      standard	   none
<	               little-endian                  standard     none
>	                big-endian	                  standard     none
!	           network (= big-endian)             standard	   none
```
Use sys.byteorder to check the endianness of your system.
```
import sys
sys.byteorder
'little'
```

```
import struct 
  
# '?' -> _BOOL , 'h' -> short, 'i' -> int and 'l' -> long 
var = struct.pack('?hil', True, 2, 5, 445) 
print(var) 
  
# struct.unpack() return a tuples 
# Variables V1, V2, V3,.. are returned as elements of tuple 
tup = struct.unpack('?hil', var) 
print(tup) 
  
# q -> long long int and f -> float 
var = struct.pack('qf', 5, 2.3) 
print(var) 
tup = struct.unpack('qf', var) 
print(tup) 
```

# Pprint
The pprint module provides a capability to “pretty-print” arbitrary Python data structures 
in a form which can be used as input to the interpreter. 
If the formatted structures include objects which are not fundamental Python types, 
the representation may not be loadable.

The formatted representation keeps objects on a single line if it can, 
and breaks them onto multiple lines if they don’t fit within the allowed width
```
class pprint.PrettyPrinter(indent=1, width=80, depth=None, stream=None, *, compact=False)
```
```
>>> import pprint
>>> stuff = ['spam', 'eggs', 'lumberjack', 'knights', 'ni']
>>> stuff.insert(0, stuff[:])
>>> pp = pprint.PrettyPrinter(indent=4)
>>> pp.pprint(stuff)
[   ['spam', 'eggs', 'lumberjack', 'knights', 'ni'],
    'spam',
    'eggs',
    'lumberjack',
    'knights',
    'ni']
>>> pp = pprint.PrettyPrinter(width=41, compact=True)
>>> pp.pprint(stuff)
[['spam', 'eggs', 'lumberjack',
  'knights', 'ni'],
 'spam', 'eggs', 'lumberjack', 'knights',
 'ni']
>>> tup = ('spam', ('eggs', ('lumberjack', ('knights', ('ni', ('dead',
... ('parrot', ('fresh fruit',))))))))
>>> pp = pprint.PrettyPrinter(depth=6)
>>> pp.pprint(tup)
('spam', ('eggs', ('lumberjack', ('knights', ('ni', ('dead', (...)))))))
```
The pprint module also provides several shortcut functions:
```
pprint.pformat(object, indent=1, width=80, depth=None, *, compact=False)
pprint.pprint(object, stream=None, indent=1, width=80, depth=None, *, compact=False)
pprint.isreadable(object)
pprint.isrecursive(object)
pprint.saferepr(object)
```
