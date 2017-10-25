# Python
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
vars(object)                                 ---> object can be module, class, instance or any object having __dict__ attribute
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
%=                                                 ---> performs modulus on the variable, with the variable then being set to the result
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

## '/','./','../'
```
/   -Root directory
./  -current working directory 
../ -parent directory, respectively
