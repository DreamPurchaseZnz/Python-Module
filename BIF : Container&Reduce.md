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
###List

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
## Reduce
Apply function of two arguments cumulatively to the items of sequence
```
reduce(lambda x, y: x+y, [1, 2, 3, 4, 5]) calculates ((((1+2)+3)+4)+5)
```

