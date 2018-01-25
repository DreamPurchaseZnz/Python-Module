# [Build-in-Functions(67)](https://docs.python.org/3/library/functions.html)
	
## commenly used
```
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
enumerate()	
int()	
bool()	
filter()	
super()
float()	
tuple()
map()	
sorted()
sum() 
```
### divmod
Take two (non complex) numbers as arguments 
and return a pair of numbers consisting of their quotient and remainder when using integer division
```
divmod(a, b)   # the result is the same as (a // b, a % b)
```
### exit
Objects that when printed, print a message like “Use quit() or Ctrl-D (i.e. EOF) to exit”, 
and when called, raise SystemExit with the specified exit code.

### dir() does much more than look up __dict__
Look here:[stackoverflow](https://stackoverflow.com/questions/14361256/whats-the-biggest-difference-between-dir-and-dict-in-python)


## other method
```
ascii()	
input()	
oct()	
staticmethod()
bin()	
eval()	
exec()	
ord()	
bytearray()	
issubclass()	
pow()	
bytes()	
iter()		
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
reversed()	
__import__()
complex()	
hasattr()	
delattr()	
hash()	
memoryview()	
set()
```
```
n=int(input("Enter the lenght of the rectangle: "))
m=int(input("Enter the width: "))
c="c"
def print_rect(n, m, c):
    for a in range(m):
        print (n*c)
print_rect(n, m, c)
input("Press enter to close")
Enter the lenght of the rectangle: >? 12
Enter the width: >? 15
cccccccccccc
...
Press enter to close
```

## open- write string to txt file
Open file and return a corresponding file object. If the file cannot be opened, an OSError is raised
```
open(
file,            --> a path-like object giving the pathname
mode='r',        --> is an optional string that specifies the mode in which the file is opened.
buffering=-1,    --> is an optional integer used to set the buffering policy.
encoding=None, 
errors=None, 
newline=None,
closefd=True, 
opener=None)
```
```
'r' open for reading (default)
'w' open for writing, truncating the file first
'x' open for exclusive creation, failing if the file already exists
'a' open for writing, appending to the end of the file if it exists
'b' binary mode
't' text mode (default)
'+' open a disk file for updating (reading and writing)
'U' universal newlines mode (deprecated)
```
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
[Using % and str.format for great good!](https://pyformat.info/#named_placeholders)

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

# Math
[Mathematical functions](https://docs.python.org/3/library/math.html)

