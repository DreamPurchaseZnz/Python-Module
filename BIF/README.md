# [Build-in-Functions(67)](https://docs.python.org/3/library/functions.html)

## dir Vs __dict__

dir() is a powerful inbuilt function in Python3, which returns 
```
list of the attributes and 
            methods of any object 
```
say functions , modules, strings, lists, dictionaries etc.

[stackoverflow](https://stackoverflow.com/questions/14361256/whats-the-biggest-difference-between-dir-and-dict-in-python)
The same applies to many built-in types; lists do not have a \_\_dict\_\_ attribute,
but you can still list all the attributes using dir():
```
>>> [].__dict__
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'list' object has no attribute '__dict__'
>>> dir([])
['__add__', '__class__', '__contains__', '__delattr__'
```
dir() doesn't just look up an object's \_\_dict\_\_ (which sometimes doesn't even exist), it will use the object's heritage (its class or type, and any superclasses, or parents, of that class or type) to give you a complete picture of all available attributes.

An instance \_\_dict\_\_ is just the 'local' set of attributes on that instance, and does not contain every attribute available on the instance. Instead, you need to look at the class and the class's inheritance tree too.



## ALL 
```
abs                                                
max                                                 
round                                               
min                                                 
len                                                 
open                                               
print                                            
format                                  
list                                     
range                                 
zip                                            
isinstance                                         
type                               
str
dict                      
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
set()                                     ---> to create a unordered collections
```

#### BIF: divmod
Take two (non complex) numbers as arguments 
and return a pair of numbers consisting of their quotient and remainder when using integer division
```
divmod(a, b)   # the result is the same as (a // b, a % b)
```
#### BIF: exit
Objects that when printed, print a message like “Use quit() or Ctrl-D (i.e. EOF) to exit”, 
and when called, raise SystemExit with the specified exit code.


#### BIF: zip()

#### BIF: enumerate()
return an enumerate object. *iterable* must be a sequence, an iterator.
```
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
list(enumerate(seasons))
Out[15]: 
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
```
 
#### BIF: input
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

#### BIF: [open- write string to txt file](https://learnpythonbreakpython.com/?s=c10)
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
#### BIF: [max](https://www.programiz.com/python-programming/methods/built-in/max)
```
max(
iterable,           --> sequence, collection
*[, key,            --> key function where the iterables are pass and 
                        comparision is performed based on its return value
default
])
```
Return the the large item in an iterable or the largest of two or more argument. the *key* argument specifies a
one-argument ordering function. 
```
max(
arg1,               --> mandatory first object for comparision
arg2,               --> mandatory second object
*args[, 
key])
```
```
print('Maximum is:', max(1, 3, 2, 5, 4))
Maximum is: 5


def sumDigit(num):
    sum = 0
    while(num):
        sum += num % 10
        num = int(num / 10)
    return sum
print('Maximum is:', max(100, 321, 267, 59, 40, key=sumDigit))
Maximum is: 267


num = [15, 300, 2700, 821]
num1 = [12, 2]
num2 = [34, 567, 78]
# using max(iterable, *iterables, key)
print('Maximum is:', max(num, num1, num2, key=len))
Maximum is: [15, 300, 2700, 821]

```


# Math
[Mathematical functions](https://docs.python.org/3/library/math.html)

