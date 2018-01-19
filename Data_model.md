# [Data model](https://docs.python.org/3/reference/datamodel.html#special-method-names)
## Objects, values and types
**Objects**: are Python’s abstraction for data. All data in a Python program is represented by objects or by relations between objects. (In a sense, and in conformance to Von Neumann’s model of a “stored program computer,” code is also represented by objects.)

**Type and Value**: Every object has an identity. An object’s identity never changes once it has been created; you may think of it as the object’s address in memory. 
> is operator: compares the identity of two objects; 
> id() function: returns an integer representing its identity.
> type() function: returns an object’s type (which is an object itself). Like its identity, an object’s type is also unchangeable
```
a = "I am Unique"
b = a
b is a # True
id(a)  # 78441968
id(b)  # 78441968
```
**CPython implementation detail**: For CPython, id(x) is the memory address where x is stored.

**Garbage-collected**:Objects are never explicitly destroyed; however, when they become unreachable they may be garbage-collected. An implementation is allowed to postpone garbage collection or omit it altogether — it is a matter of implementation quality how garbage collection is implemented, as long as no objects are collected that are still reachable.
```
close(): provide an explicit way to release the external resource
Programs are strongly recommended to explicitly close such objects
with
try…finally statement 
try…except statement   : may keep objects alive
```

## The standard type hierarchy
Below is a list of the types that are built into Python

**Theme**: Some of the type descriptions below contain a paragraph listing ‘special attributes.’

### numbers.Number
arithmetic operators and arithmetic built-in functions
```
numbers.Integral
numbers.Real (float)
numbers.Complex (complex)
```
### Sequences
> Immutable sequences: Strings, Tuples, Bytes
> Mutable sequences: Lists, Byte Arrays

When the length of a sequence is n, then as the following 
```
len(): returns the number of items of a sequence. 
the index set contains the numbers 0, 1, …, n-1. 

Item i of sequence a is selected by a[i].

slicing: 
a[i:j] selects all items with index k such that i <= k < j. 

extended slicing with a third “step” parameter: 
a[i:j:k] selects all items of a with index x where x = i + n*k, n >= 0 and i <= x < j.
```
### Set types
These represent unordered, finite sets of unique, immutable objects. 

As such, they cannot be indexed by any subscript. However, they can be iterated over, and the built-in function len() returns the number of items in a set. Common uses for sets are fast membership testing, removing duplicates from a sequence, and computing mathematical operations such as intersection, union, difference, and symmetric difference.

> Sets and Frozen sets

### Mappings
These represent finite sets of objects indexed by arbitrary index sets. The subscript notation a[k] selects the item indexed by k from the mapping a; this can be used in expressions and as the target of assignments or del statements. The built-in function len() returns the number of items in a mapping.

There is currently a single intrinsic mapping type:
> Dictionaries: these represent finite sets of objects indexed by nearly arbitrary values. 

Dictionaries are mutable; they can be created by the {...} notation 

### Callable types
These are the types to which the function call operation (see section Calls) can be applied:

**User-defined functions**: A user-defined function object is created by a function definition (see section Function definitions). It should be called with an argument list containing the same number of items as the function’s formal parameter list.

Special attributes:
```
__doc__
__name__
__qualname__
__module__
__defaults__
__code__
__globals__
__dict__
__closure__	
__annotations__
__kwdefaults__
```
A simple example for Explanation
```
def use_function(a, b=1, sentence="Hi, there"):
    """Just for explanation"""
    print(sentence)
    return a + b
```
```
use_function.__doc__         # 'Just for explanation'
use_function.__name__        # 'use_function'
use_function.__defaults__    # (1, 'Hi, there')
use_function.__kwdefaults__
use_function.__qualname__    # 'use_function'
use_function.__module__      # '__main__'
use_function.__globals__     # all the variable in the namescope
```

### instance method
An instance method object combines a class, a class instance and any callable object (normally a user-defined function)


### Built-in functions & Built-in methods

### Modules
**Modules** : are a basic organizational unit of Python code, and are created by the import system as invoked either by the import statement (see import), or by calling functions such as importlib.import_module() and built-in \__import\__(). 

Attribute references are translated to lookups in this dictionary, e.g., m.x is equivalent to m.\__dict\__["x"]. A module object does not contain the code object used to initialize the module (since it isn’t needed once the initialization is done).

Attribute assignment updates the module’s namespace dictionary, e.g., m.x = 1 is equivalent to m.\__dict\__["x"] = 1
```
__dict__ : Special read-only attribute; is the module’s namespace as a dictionary object.
__name__ : is the module’s name;
__doc__  : is the module’s documentation string, or None if unavailable; 
__annotations__ (optional): is a dictionary containing variable annotations collected during module body execution; 
__file__ : is the pathname of the file from which the module was loaded, if it was loaded from a file. 
```
```
import tensorflow as tf
tf.__file__
Out[134]: 
'C:\\Program Files\\Anaconda3\\lib\\site-packages\\tensorflow\\__init__.py'
tf.__doc__
tf.__dict__
Out[136]: 
{'AggregationMethod': tensorflow.python.ops.gradients_impl.AggregationMethod,
 'Assert': <function tensorflow.python.ops.control_flow_ops.Assert>,
 'AttrValue': tensorflow.core.framework.attr_value_pb2.AttrValue,
 'COMPILER_VERSION': 'MSVC',
 'ConditionalAccumulator': tensorflow.python.ops.data_flow_ops.ConditionalAccumulator,
 'ConditionalAccumulatorBase': tensorflow.python.ops.data_flow_ops.ConditionalAccumulatorBase,
 'ConfigProto': tensorflow.core.protobuf.config_pb2.ConfigProto,
 'DType': tensorflow.python.framework.dtypes.DType,
 'DeviceSpec': tensorflow.python.framework.device.DeviceSpec,
 'Dimension': tensorflow.python.framework.tensor_shape.Dimension,
 'Event': tensorflow.core.util.event_pb2.Event,

```
### Custom classes
Custom class types are typically created by class definitions (see section Class definitions). A class has a namespace implemented by a dictionary object. 

Special attributes:
```
 __name__ : is the class name;
 __module__: is the module name in which the class was defined; 
 __dict__ : is the dictionary containing the class’s namespace; 
 __bases__: is a tuple containing the base classes, in the order of their occurrence in the base class list;
 __doc__ : is the class’s documentation string, or None if undefined; 
 __annotations__: (optional) is a dictionary containing variable annotations collected during class body execution.
```

### Class instances
A class instance is created by calling a class object (see above). A class instance has a namespace implemented as a dictionary which is the first place in which attribute references are searched.

Special attributes:
```
__dict__: is the attribute dictionary; 
__class__: is the instance’s class.
```

### I/O objects (also known as file objects)
A file object represents an open file. Various shortcuts are available to create file objects: 
```
open(): built-in function, and also 
os.popen() :
os.fdopen(): 
makefile() method of socket objects
```
The objects sys.stdin, sys.stdout and sys.stderr are initialized to file objects corresponding to the interpreter’s standard input, output and error streams; they are all open in text mode and therefore follow the interface defined by the io.TextIOBase abstract class.

### Internal types
A few types used internally by the interpreter are exposed to the user.
```
Code objects
Frame objects
Traceback objects
Slice objects
Static method objects
Class method objects
```





## Special method names -Magic Method(Explained another chapter)

