# Container
--------------------------------------------------------------------------
[This module implements specialized container datatypes providing alternatives to Python’s general purpose built-in containers, dict, list, set, and tuple.](https://docs.python.org/3.5/library/collections.html?highlight=defaultdict#collections.defaultdict)
```
namedtuple                        
deque          
ChainMap          
Counter          
OrderedDict          
defaultdict                                               ---> dict subclass that calls a factory function to supply missing values
UserDict         
UserList          
UserString          
```
### defaultdict
return a new dictionary-like object. 
It ignores a method and add a writable instance variable. the function is same as **dict**(key-value pair):
```
__missing__(key)
default_factory                                       ---> Key type argument(list,set,int...)         
``` 

Dict Operation Supported
```
len
d[key]
get(key)
d[key] = value
setdefault                                           ---> If not, insert key with a value of default 

# Delete operation                                                        
del d[key]
pop                                                 
popitem
clear
copy

# Acquire information
key in d                                            ---> True if key exists
key not in d
iter                                                ---> For in iterations

# Get value
fromkeys
update                                              ---> Update the dictionary with the key/value pairs from other
items                                               ---> View objects 
values                                              ---> Dynamic view on dictionary'entries
keys                                                ---> Iteration
```
e.g.
```
from collections import defaultdict
s = [('yellow', 1), ('blue', 2), ('yellow', 3), ('blue', 4), ('red', 1)] # iterable
d = defaultdict(list) # Given a type
for k, v in s:
  d[k].append(v)      # List Append method to dict value
  
sorted(d.items())
```
### List

All of the methods of list objects
```
append                                   ---> Add an item to the end of the list
extend                                   ---> Extend the list by appending all the items in the given list
insert                                   ---> Insert an item at a given position 
remove                                   ---> Remove the first item from the list whose value is x
pop                                      ---> Remove the item at the given position in the list, and return it
index                                    ---> Return the index in the list of the first item whose value is x
count                                    ---> Return the number of times x appears in the list
sort                                     ---> Sort the items of the list in place
reverse                                  ---> Reverse the elements of the list, in place
```
append:
add an item to the end of the list; equivalent to a[len(a):]=[x]
```
x = [1,2,3]
x.append([4,5])
print(x)
Out[14]: 
[1, 2, 3, [4, 5]]
```
```
x = [1,2,3]
x[len(x):]=[4]
x
Out[25]: 
[1, 2, 3, 4]

```

list.extend(seq)- This method does not return any value but add the content to existing list

Extend the list by appending all the items in the given list; equivalent to a[len(a):] = L
```
x.extend([4,5])
x
Out[18]: 
[1, 2, 3, [4, 5], 4, 5]
```
```
x[len(x):]=[4,5]
x
Out[28]: 
[1, 2, 3, 4, 4, 5]

```

```
aList = [123, 'xyz', 'zara', 'abc', 123];
bList = [2009, 'manni'];
aList.extend(bList)
aList
Out[20]: 
[123, 'xyz', 'zara', 'abc', 123, 2009, 'manni']

```
when it comes to the numpy array, the append/extend method can't be used to append/extend
it by attribute.
```
import numpy as np
c['e'].append(np.array([1,2]))
c['e']
Out[16]: 
[array([1, 2])]
c['e'].append(np.array([1,2]))
c['e']
Out[18]: 
[array([1, 2]), array([1, 2])]
c['e'][1]
Out[19]: 
array([1, 2])
c['e'][1].append([4,5])
AttributeError: 'numpy.ndarray' object has no attribute 'append'
```
np.append method can be used for this situation
```
c['e'][1]=np.append(4, c['e'][1])
c['e'][1]
Out[23]: 
array([4, 1, 2])
c['e'][1]=np.append(c['e'][1],[4,5])
c['e'][1]
Out[25]: 
array([4, 1, 2, 4, 5])


```


## Reduce
Apply function of two arguments cumulatively to the items of sequence
```
import functools as ft
ft.reduce(lambda x, y: x+y, [1, 2, 3, 4, 5]) calculates ((((1+2)+3)+4)+5)
```
## Reload a module
```
from importlib import reload
reload(module)
```
