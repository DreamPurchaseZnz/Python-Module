# [Build-in-Functions(67)](https://docs.python.org/3/library/functions.html)
	
## ALL 
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

## BIF: divmod
Take two (non complex) numbers as arguments 
and return a pair of numbers consisting of their quotient and remainder when using integer division
```
divmod(a, b)   # the result is the same as (a // b, a % b)
```
## BIF: exit
Objects that when printed, print a message like “Use quit() or Ctrl-D (i.e. EOF) to exit”, 
and when called, raise SystemExit with the specified exit code.

## BIF: dir() does much more than look up __dict__
Look here:[stackoverflow](https://stackoverflow.com/questions/14361256/whats-the-biggest-difference-between-dir-and-dict-in-python)

## zip()

## enumerate()
return an enumerate object. *iterable* must be a sequence, an iterator.
```
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
list(enumerate(seasons))
Out[15]: 
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
```
 
## input
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

## [open- write string to txt file](https://learnpythonbreakpython.com/?s=c10)
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



# Math
[Mathematical functions](https://docs.python.org/3/library/math.html)

