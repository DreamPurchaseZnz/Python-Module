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
### exit()
Objects that when printed, print a message like “Use quit() or Ctrl-D (i.e. EOF) to exit”, 

and when called, raise SystemExit with the specified exit code.

## open- write string to txt file
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
Perform a string [formatting operation](https://docs.python.org/3.5/library/functions.html?highlight=format#format)
The string on which this method is called can contain literal text or replacement fields delimited by braces {}.
Each replacement field contains either the numeric index of a positional argument, or the name of a keyword argument.
Returns a copy of the string where each replacement field is replaced with the string value of the corresponding argument.
(Using % and str.format for great good!)[https://pyformat.info/#named_placeholders]

The general form of a standard format specifier is
```
format_spec ::=  [[fill]align][sign][#][0][width][,][.precision][type]
```
```
fill        ::=  <any character>
align       ::=  “<” | “>” | “=” | “^”
sign        ::=  “+” | “-” | ” “
width       ::=  integer
precision   ::=  integer
type        ::=  “b” | “c” | “d” | “e” | “E” | “f” | “F” | “g” | “G” | “n” | “o” | “s” | “x” | “X” | “%”
```

In most of the cases the syntax is similar to the old %-formatting, with the addition of the {} <br>
and with : used instead of %. For example, '%03.2f' can be translated to '{:03.2f}'

The meaning of the various alignment options is as follows:
```
<           ::= Left-aligned
>           ::= Right-aligned
=           ::= Padding after the sigh
^           ::= Center-aligned
```

The sign option is only valid for number types, and can be one of the following:
```
+           ::= Both positive and negative
_           ::= Negative only
space       ::= Space on positive and minus sign on negative number
```
The '#' option is only valid for integers, and only for binary, octal, or hexadecimal output.
If present, it specifies that the output will be prefixed by '0b', '0o', or '0x', respectively

The ',' option signals the use of a comma for a thousands separator.
For a locale aware separator, use the 'n' integer presentation type instead.

###  Comparison with the old %-formatting
In most of the cases the syntax is similar to the old %-formatting, 
with the addition of the {} and with : used instead of %. For example, '%03.2f' can be translated to '{:03.2f}'
The new format syntax also supports new and different options

1. Accessing arguments by 
```
position
name
attributes
items
```
2. Replacing %s and %r
```
"repr() shows quotes: {!r}; str() doesn't: {!s}".format('test1', 'test2')
```
3. Aligning the text and specifying a width:
```
>>'{:*^30}'.format('centered')  # use '*' as a fill char
>>'***********centered***********'
```
4. Replacing %+f, %-f, and % f and specifying a sign

5. Replacing %x and %o and converting the value to different bases

6. Using the comma as a thousands separator

7. Expressing a percentage
```
>>> points = 19.5
>>> total = 22
>>> 'Correct answers: {:.2%}'.format(points/total)
'Correct answers: 88.64%'
```
8. Using type-specific formatting

# Print
```
print(value, ..., sep=' ', end='\n', file=sys.stdout)
```
```
Prints the values to a stream, or to sys.stdout by default.
Optional keyword arguments:
file: a file-like object (stream); defaults to the current sys.stdout.
sep:  string inserted between values, default a space.
end:  string appended after the last value, default a newline.

```
