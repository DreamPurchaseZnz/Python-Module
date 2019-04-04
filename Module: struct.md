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
