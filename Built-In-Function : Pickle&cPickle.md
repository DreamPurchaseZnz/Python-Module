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
