# Container
--------------------------------------------------------------------------
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
