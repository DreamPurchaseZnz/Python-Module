Pickle & cPickle
-----------------------------------------------------------------------------------------
### Relationship to other python modules
Pickle Module implements an algorithm for turning an arbitrary python object into a series of bytes.
this progress is also called *serializing* the object. The byte stream representing the object can then be transmitted or stored, and later reconstructed to create a new object with the same characteristics

The cPickle module implements the same algorithm, in C instead of Python. 
It is many times faster than the Python implementation, but does not allow the user to subclass from Pickle.
If subclassing is not important for your use, you probably want to use cPickle

Note:On python3.x cPickle has changed from cPickle to **_pickle**. Thus in python3.x, you can do the following if you want to use cPickle
### Data stream format
There are currently 3 different protocols which can be used for pickling
```
Protocol version 0                                ---> Original ASCII protocol 
Protocol version 1                                ---> The old binary format 
Protocol version 2                                ---> It provides much more efficient pickling of new-style classes.
```
### Usage:
To serialize an object hierarchy, you first create a pickler, then you call the pickler’s dump() method.

To de-serialize a data stream, you first create an unpickler, then you call the unpickler’s load() method. 

The pickle module provides the following constant:
```
pickle.HIGHEST_PROTOCOL
```
```
pickle.dump                                      ---> Write a pickled representation of obj to the open file object file
pickle.load                                      ---> Read a string from the open file object file and interpret it as a pickle data stream
pickle.dumps                                     ---> Representation of the object is a string, instead of writing it to a file
pickle.loads                                     
```
Exports two callables
```
pickle.Pickler                                   ---> Pickler(file, protocol).dump(obj)
pickle.Unpickler                                 ---> Unpickler(file).load()
```
e.g.
```
open(rgan_dir+'/rgan_pickle.pkl','wb')           ---> Write
open(rgan_dir+'/rgan_pickle.pkl','rb')           ---> Read
```

## what if it's two object 
there are two method
**First method**
pickle.dump will append to the end of the file, so you can call it multiple times to write multiple values.

pickle.load will read only enough from the file to get the first value, leaving the filehandle open and pointed at the start of the next object in the file. The second call will then read the second object, and leave the file pointer at the end of the file. A third call will fail with an EOFError as you'd expect.

```
import pickle

# write a file
f = open("example", "w")
pickle.dump(["hello", "world"], f)
pickle.dump([2, 3], f)
f.close()

f = open("example", "r")
value1 = pickle.load(f)
value2 = pickle.load(f)
f.close()

```
** second method**
 pack your data into a single object before you store it
```
a = [1,2]
b = [3,4]

with open("tmp.pickle", "wb") as f:
    pickle.dump((a,b), f)

with open("tmp.pickle", "rb") as f:
    a,b = pickle.load(f) 
```

# Json
lightweight data interchange liberary

## Basic usage
```
json.dump(obj, fp, skipkeys=False, ensure_ascii=True, check_circular=True, allow_nan=True, cls=None, indent=None, separators=None, encoding=”utf-8”, default=None, sort_keys=False, **kw)
```
```
obj                              ---> object
fp                               ---> File_name
skipkeys                         ---> Not of a basic type Don't raise error
ensure_ascii                     ---> all non-ASCII characters in the output are escaped
check_circular
allow_nan                        ---> out of range float values (nan, inf, -inf) Raise Value error
indent                           ---> non-negative integer, pretty-printed with that indent level
separators                       ---> separators should be an (item_separator, key_separator) tuple. By default, (', ', ': ')
encoding                         ---> UTF-8
default                          ---> should be a function that gets called for objects that can’t otherwise be serialized
sort_keys                        ---> the output of dictionaries will be sorted by key
```

