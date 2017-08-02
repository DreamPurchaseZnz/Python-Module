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
## Open()- write string to txt file
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
text_file = open("path/name.txt", "w")
text_file.write("discription : %s" % variable)
text_file.close()
```
if you use a context manager ,the file is closed automatically for you
```
with open('path/name.text','w') as text_file:
   text_file.write('discription:{}'.format{variables})
```
Also we can write many lines at once.
```
with open('name.txt','w') as writer:
    lines = ['line 1\n',
            'this is line 2\n'
            'this is line 3\n'
            'this is end']
    writer.writelines(lines)

file_text = open('name.txt','r')
print(file_text.read())      
```

## format()- present formatted value



