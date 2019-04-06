# Python
## [Working with files](https://realpython.com/working-with-files-in-python/)

### Filename pattern matching
These are methods and functions available to you:
```
endswith() and startswith() string methods
fnmatch.fnmatch()
glob.glob()
pathlib.Path.glob()
```
#### Using string methods
```
>>> import os

>>> # Get .txt files
>>> for f_name in os.listdir('some_directory'):
...     if f_name.endswith('.txt'):
...         print(f_name)
```
#### simple filename pattern matching  using fnmatch
```
>>> import os
>>> import fnmatch

>>> for file_name in os.listdir('some_directory/'):
...     if fnmatch.fnmatch(file_name, '*.txt'):
...         print(file_name)
```
#### Filename Pattern Matching Using glob
```
>>> import glob
>>> glob.glob('*.py')
['admin.py', 'tests.py']
```

## Reading and Writing Files
### Open file with specific mode
The built-in python function open has the following arguments
```
open(
file,                        # basically is the path where your file resides, if at current directory,
                               just provide the name 
mode='r', 
buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)
```
```
r                   # Open file for reading only. 
                      Starts reading from beginning of file. This default mode.
rb	                 # Open a file for reading only in binary format. 
                      Starts reading from beginning of file.
r+	                 # Open file for reading and writing. 
                      File pointer placed at beginning of the file.
w	                  # Open file for writing only. File pointer placed at beginning of the file. 
                      Overwrites existing file and creates a new one if it does not exists.
wb	                 # Same as w but opens in binary mode.
w+	                 # Same as w but also alows to read from file.
wb+	                # Same as wb but also alows to read from file.
a	                  # Open a file for appending. 
                      Starts writing at the end of file. Creates a new file if file does not exist.
ab	                 # Same as a but in binary format. Creates a new file if file does not exist.
a+	                 # Same a a but also open for reading.
ab+	                # Same a ab but also open for reading.
```
### Read from a file
```
read([n])                   # n is the number of bytes to be read
readline([n])               # n is the number of bytes in a line to be read
readlines()
```
if read() without any argument, just output the entire file

You can read the file line by line using a for loop
```
f = open(file, "r")
for line in f:
  print(line)
  
f.close
```
Readlines() method maintains a list of each line in the file.
```
f=open(file, "r")
f.readlines()
```


### Closing a file
When you see a close() method, you will clear all the buffer and close the file
```
myfile.close()
```

### Writing to a file
```
write(string) (for text) or write(byte_string) (for binary)
writelines(list)
```
```
new_file=open("D:\\new_dir\\newfile.txt",mode="w",encoding="utf-8")
new_file.write("Writing to a new file\n")
new_file.write("Writing to a new file\n")
new_file.write("Writing to a new file\n")
new_file.close()
```
Note that reading from a file does not print anything because the file cursor is at the end of the file. To set the cursor at the beginning, you can use the seek() method of file object:
```
cars=["Audi\n","Bentely\n","Toyota\n"]
new_file=open("D:\\new_dir\\newfile.txt",mode="a+",encoding="utf-8")
for car in cars:
    new_file.write(car)
print("Tell the byte at which the file cursor is:",new_file.tell())
new_file.seek(0)
for line in new_file:
    print(line)
```
The tell() method of file object tells at which byte the file cursor is located. In seek(offset,reference_point) the reference points are 0 (the beginning of the file and is default), 1 (the current position of file) and 2 (the end of the file).

Note the use of .seek() and .truncate(): the argument in .truncate() is 5 that says that truncate the file till 5 bytes of text are left. And output shows exactly 5 bytes of text left including space. You are only left with next() method so let's complete this section of the tutorial! Here you are using same file created above with name multiplelines.txt.


### Json file
objects consists of keys and values.
```
{
"Algeria":"Algiers",
"Andorra":"Andorra la Vella",
"Nepal":"Kathmandu",
"Netherlands":"Amsterdam",
}
```
```
json.dump
json.load
```

### Python file object attributes
```
name             # Returns the name of the file
closed           # Returns true if file is closed. False otherwise.
mode             # The mode in which file is open.
softspace        # Returns a Boolean that indicates whether a space character 
                   needs to be printed before another value when using the print statement.
encoding         # The encoding of the file
```

### Handling files through os module
perform Operating System dependent operations such as making a folder, 
listing contents of a folder, know about a process, end a process etc.
```
os.makedirs()              # Create a new folder
os.listdir()               # List the contents of a folder
os.getcwd()                # Show current working directory
os.path.getsize()          # show file size in bytes of file passed in parameter
os.path.isfile()           # Is passed parameter a file
os.path.isdir()            # Is passed parameter a folder
os.chdir                   # Change directory/folder
os.rename(current,new)     # Rename a file
os.remove(file_name)       # Delete a file
```


## Check the list of detailed function of a particular module
use the command
```
__dict__
```
**for example**
```
import math
math.__dict__
```
```
'__doc__': 'This module is always available.  It provides access to the\nmathematical functions defined by the C standard.',
 '__loader__': _frozen_importlib.BuiltinImporter,
 '__name__': 'math',
 '__package__': '',
 '__spec__': ModuleSpec(name='math', loader=<class '_frozen_importlib.BuiltinImporter'>, origin='built-in'),
 'acos': <function math.acos>,
 'acosh': <function math.acosh>,
 'asin': <function math.asin>,

...

```


## Python syntax- if & for
That's more specifically a ternary operator expression than an if-then, here's the python syntax
```
value_when_true if condition else value_when_false
[value_false, value_true][<test>]
[lambda: value_false, lambda: value_true][<test>]()
[Loop value for i in range(size)]
```
e.g.
```
count = 0 if count == N else N + 1
count = [0,N+1][count==N]
count = [lambda:0, lambda:N+1][count==N]()
```
e.g.
```
f = [e for e in range(10) for _ in range(10)]),[sample_size,1]
```
## unpacks an dictionary into keyword arguments

```
list or tupe  --- * unpack ---> call function --- positional argument  --- function --- * collects ---> a tupe
a dictionary --- ** unpack  ---> call function --- keyword argument --- function --- ** collects ---> a dictionary 
```
### Inside a function header
```
*    ---> collects all the positional arguments in a tuple
**   ---> collects all the keyword arguments in a dictionary
```
```
>>> def functionA(*a, **kw):
       print(a)
       print(kw)


>>> functionA(1, 2, 3, 4, 5, 6, a=2, b=3, c=5)
(1, 2, 3, 4, 5, 6)
{'a': 2, 'c': 5, 'b': 3}
```

### In a function call:
```
* unpacks a list or tuple into position arguments
** unpacks a dictionary into keyword arguments
```
```
>>> lis=[1, 2, 3, 4]
>>> dic={'a': 10, 'b':20}
>>> functionA(*lis, **dic)  #it is similar to functionA(1, 2, 3, 4, a=10, b=20)
(1, 2, 3, 4)
{'a': 10, 'b': 20}
```
## Pack attributes to a dictionary
The syntax of vars() is:
```
vars(object)                                 ---> object can be module, class, 
                                                  instance or any object having __dict__ attribute
```
Return the \__dict__ attribute of the given object
```
class Foo:
    def __init__(self, a=5, b=10):
        self.a = a
        self.b = b
InstanceOfFoo = Foo()
print(vars(InstanceOfFoo))
{'b': 10, 'a': 5}
```
```
Foo.__dict__
Out[36]: 
mappingproxy({'__dict__': <attribute '__dict__' of 'Foo' objects>,
              '__doc__': None,
              '__init__': <function __main__.Foo.__init__>,
              '__module__': '__main__',
              '__weakref__': <attribute '__weakref__' of 'Foo' objects>})
InstanceOfFoo.__dict__
Out[37]: 
{'a': 5, 'b': 10}
```

## Operator - cumulative by stride 
```
-=                                                 ---> subtracts a value from variable, setting the variable to the result
*=                                                 ---> multiplies the variable and a value, making the outcome the variable
/=                                                 ---> divides the variable by the value, making the outcome the variable
%=                                                 ---> performs modulus on the variable,
                                                        with the variable then being set to the result
```

## Colon':'
: is the delimiter of the slice syntax to 'slice out' sub-parts in sequences , [start:end]

It's pretty simple really:
```
a[start:end] # items start through end-1
a[start:]    # items start through the rest of the array
a[:end]      # items from the beginning through end-1
a[:]         # a copy of the whole array
```
There is also the step value, which can be used with any of the above:
```
a[start:end:step] # start through not past end, by step
```
The key point to remember is that the :end value represents the first value that is not in the selected slice. So, the difference beween end and start is the number of elements selected (if step is 1, the default).

The other feature is that start or end may be a negative number, which means it counts from the end of the array instead of the beginning. So:
```
a[-1]    # last item in the array
a[-2:]   # last two items in the array
a[:-2]   # everything except the last two items
```
Python is kind to the programmer if there are fewer items than you ask for. For example, if you ask for a[:-2] and a only contains one element, you get an empty list instead of an error. Sometimes you would prefer the error, so you have to be aware that this may happen.


```
>>> seq[:]                # [seq[0],   seq[1],          ..., seq[-1]    ]
>>> seq[low:]             # [seq[low], seq[low+1],      ..., seq[-1]    ]
>>> seq[:high]            # [seq[0],   seq[1],          ..., seq[high-1]]
>>> seq[low:high]         # [seq[low], seq[low+1],      ..., seq[high-1]]
>>> seq[::stride]         # [seq[0],   seq[stride],     ..., seq[-1]    ]
>>> seq[low::stride]      # [seq[low], seq[low+stride], ..., seq[-1]    ]
>>> seq[:high:stride]     # [seq[0],   seq[stride],     ..., seq[high-1]]
>>> seq[low:high:stride]  # [seq[low], seq[low+stride], ..., seq[high-1]]                                   
```

## what's the meaning of '/','./' and '../'
```
/   -Root directory
./  -current working directory 
../ -parent directory, respectively
```

## what the difference of '/' , '\' and '\\'
unix and its variants have always used the forward slash(/) to donate filesystem hierachy

however windows owes its filesystem delimiter, the backslash(\) to its MS-Dos prodecessor And MS-DOS wasnt the originator of that. It was brought over from the QDOS operating system (which borrowed from CP/M), which MS bought and reworked into MS-DOS.

Since most, if not all , of web based protocols orginated on UNIX, Miscrosoft compiles with those delimiter to keep 
compatibility.
```
junkfile = open('c:/tmp/junkpythonfile','w')               
junkfile = open(r'c:\tmp\junkpythonfile','w')
junkfile = open('c:\\tmp\\junkpythonfile','w')
```


## Unnamed characteristic
```
c = np.arange(10)
c
Out[19]: 
array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
```
```
c[8:10]
Out[21]: 
array([8, 9])
```
When the index out of the range, python can also return the value in the range and won't raise a error
```
c[8:11]
Out[22]: 
array([8, 9])

```
## Maximum Recursion depth 

```
>>> a = {}
>>> b = {}
>>> a['next'] = b
>>> b['next'] = a
>>> a == b
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
RuntimeError: maximum recursion depth exceeded in cmp
```
```
>>> a
{'next': {'next': {...}}}

```
If there is a circular structure, where your dicts refer to itself through a chain of something,
```
class recursion:
   @property
   def a(self):
       if self.a is None:   
          _a = 1
   return _a
```
the function above intend to build a close subspace, to return value of a when call a,
however it'll raise a recursion error, because when you call a, 
will call the function a, the judgement of a in function will call the function again
so there is a circular loop. Finally raise the 'Maximum Recursion depth' Exception error 
It can be revised as follows:
```
class recursion:
   @property
   def a(self):
       if self._a is None:   
          self._a = 1
   return self._a
```










