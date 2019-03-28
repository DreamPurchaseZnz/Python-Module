# [Gloassary](https://docs.scipy.org/doc/numpy-1.13.0/glossary.html#term-column-major)
## along an axis
Axes are defined for arrays with more than one dimension. 
A 2-dimensional array has two corresponding axes:
> the first running vertically downwards across rows (axis 0), 
> the second running horizontally across columns (axis 1).

Many operation can take place along one of these axes.
For example, we can sum each row of an array, in which case we operate along columns, or axis 1:
```
>>> x = np.arange(12).reshape((3,4))

>>> x
array([[ 0,  1,  2,  3],
       [ 4,  5,  6,  7],
       [ 8,  9, 10, 11]])

>>> x.sum(axis=1)
array([ 6, 22, 38])
```
## attribute
a property of an object that can be accessed using obj.attribute

##  C order
See *row_major*

## column-major
A way to represent items in a N-dimensional array in 1-dimensional computer memory. 
> in column-major, the leftmost index 'vary the fastest', for example the array:
```
np.array([[1,2,3],[4,5,6]])
Out[63]: 
array([[1, 2, 3],
       [4, 5, 6]])
```
is represented in the column-major order as:
```
[1, 4, 2, 5, 3, 6]
```
Column-major order is alse known as the fortran order. used, for example, in the fortrain langage and in matlab

## row-major
A way to represent items in N-dimensional array in 1-dimensional computer memory. 
> in the row-major order, the rightmost index 'varies fastest': for example
```
[[1, 2, 3],
 [4, 5, 6]]
```
is represented in the row-major order as:
```
[1, 2, 3, 4, 5, 6]
```
row-major , used in C, thus is also known as the C order, the Numpy arrays are by default in row-major order.

> Tips: 
> reshape x= transpose
For example
```
import numpy as np
>> a = np.array([[1,2,3],[4, 5, 6]])
 
array([[1, 2, 3],
       [4, 5, 6]])
       
>> np.reshape(a, (3,2))

array([[1, 2],
       [3, 4],
       [5, 6]])
>> a.T 
array([[1, 4],
       [2, 5],
       [3, 6]])

```



## decorator
an operator that transforms a function, for example, a log decorator may be defined to print debugging information  
upon function execution:

```
def decorator_funciton(original_function):
    def wrapper_function(*args, **kwargs):
        print("Logging call with parameters:", args, kwargs)
        return original_function(*args, **kwargs)
    return wrapper_function
```
**Mechanism**: The decorator_function only take the function as the argument, then return a wrapperfunction. Therefore, you just put 
the latter argument pass to the original function. It doesn't pass through the decorator function, instead, the wrapper function take 
all the parameters and pass to the original function.

then we define a function we can decorate it using *decorator_funciton*
```
@decorator_funciton
def add(a, b):
    return a + b
```
the way is equivalent to the following original way:
```
decorated_add = decorator_funciton(add)
```
Thus the result can be:
```
add(1,2)
Logging call with parameters: (1, 2) {}
Out[12]: 
3
```
```
decorated_add(1, 2)
Logging call with parameters: (1, 2) {} # first time decorate by @ operator
Logging call with parameters: (1, 2) {}              
Out[14]: 
3
```

## dictionary

Resembling a language dictionary, which provide a mapping between words and discription thereof. 
a python dictionary ia a mapping between two objects
```
x = {1: 'one', 'two': [1, 2]}
```
Here, x is a dictionary mapping keys to values, in this case, the integer 1 to the string 'one'
the values can be acessed using their corresponding keys:
```
x[1]
Out[17]: 
'one'
x['two']
Out[18]: 
[1, 2]
```
> Note that the dictionaries are not stored in any *specific* order 

## Fortran order
See column-major oder

## flattened
collapsed to one-dimensional array

## immutable
An object that canno be modified after execution is called immutable


## instance

a class definition give blueprint for contructing an object
```
 class House(object):
     wall_colour = 'white'
```
yet we have to build a hourse after it exists:
```
h = House()
h
Out[21]: 
<__main__.House at 0x4a3fe80>
h.wall_colour
Out[22]: 
'white'
```
An instance is therefore a specific realisation of a class.

## iterable
A sequence that allows " walking "(iterating) over items. typically using a loop such as:
```
x = [1, 2, 3]
[item**2 for item in x]
Out[25]: 
[1, 4, 9]

```
**It is often used in combination with numerate:**
```
keys = ['a','b','c']
for n, k in enumerate(keys):
    print("Key %d: %s" % (n, k))
    
Key 0: a
Key 1: b
Key 2: c
```
## List
A python container that can hold any number of objects or items. The items do not have to be of the same type,
and can even be lists themselves:
```
x = [2, 2.0, "two", [2, 2.0]]
x
Out[29]: 
[2, 2.0, 'two', [2, 2.0]]
```
The list x contains 4 items, each which can be accessed individually:
```
x[2]
Out[30]: 
'two'
x[3]
Out[31]: 
[2, 2.0]
```
It is alse possible to select more that one item at a time, using *slicing*
```
x[0:2]
Out[32]: 
[2, 2.0]
```
In code, arrays are often conventiontly expressed as nested lists
```
np.array([[1, 2], [3, 4]])
```

## mask
A boolean array, used to select only certain elements for an operation:
```
x = np.arange(5)
x
Out[36]: 
array([0, 1, 2, 3, 4])
mask = (x>2)
mask
Out[38]: 
array([False, False, False,  True,  True])
x[mask] = -1
x
Out[40]: 
array([ 0,  1,  2, -1, -1])
```
## masked array

Array that suppressed values indicated by a mask
```
x = np.ma.masked_array([np.nan, 2, np.nan], [True, False, True])
x
Out[42]: 
masked_array(data=[--, 2.0, --],
             mask=[ True, False,  True],
       fill_value=1e+20)
x + [1, 2, 3]
Out[43]: 
masked_array(data=[--, 4.0, --],
             mask=[ True, False,  True],
       fill_value=1e+20)
```
Masked arrays are often used when operating on arrays containing missing or invalid entries.

## matrix
A 2 dimensional array that preseves its two-dimensional nature throughout operations. It has certain special operation, 
such as * (matrix multiplication)
and ** (matrix power), defined:
```
x = np.mat([[1, 2], [3, 4]])
x
Out[45]: 
matrix([[1, 2],
        [3, 4]])
x**2
Out[46]: 
matrix([[ 7, 10],
        [15, 22]])


```
## method
A function associated with an object. for example, each ndarray has a method called repeat.
```
x = np.array([1, 2, 3])
x.repeat(2)
Out[48]: 
array([1, 1, 2, 2, 3, 3])
```
## reference
if a is a reference to b, then **(a is b) == True**. Therefore, a and b are different names for the same python object
```
x = np.array([1, 2, 3])
x.repeat(2)
Out[48]: 
array([1, 1, 2, 2, 3, 3])
y = x
y is x
Out[50]: 
True
```
## row major
A way to represent items in a N-dimensional array in the 1-dimensional computer memory. In row-major order, the rightmost index “varies the fastest”: for example the array:

```
[[1, 2, 3],
 [4, 5, 6]]
```
is represented in the row-major order as:
```
[1, 2, 3, 4, 5, 6]
```
Row-major order is also known as the C order, as the C programming language uses it. New NumPy arrays are by default in row-major order.

## self
Often see in method signatures, self refers to the instance of the associated class
```
class paintbrush:
    def __init__(self, color):
        self.color = color
    def paint(self):
        print("Paint the city {}".format(self.color))
                
                
p = paintbrush('red')       ---> instance red of the class paintbrush
p.color                     ---> so python will pass the p, the instance, to color.
Out[53]: 
'red'
p.paint()
Paint the city red
```
## slice
Used to select only certain elements from a sequence.
```
x = range(5) 
list(x)
Out[57]: 
[0, 1, 2, 3, 4]
list(x[1:3]) # slice from 1 to 3(excluding 3 itself)
Out[59]: 
[1, 2]
list(x[1:5:2])# slice from 1 to 5, but skipping every two second element
Out[60]: 
[1, 3]
list(x[::-1]) # slice a sequence in reverse
Out[61]: 
[4, 3, 2, 1, 0]
```
Arrays may have more than one dimension, each which can be sliced individually

## Structured data type
a data type composed of other datatypes

## tuple
A tuple is immutable,i.e., once constructed it cannot be changed. similar to a list, it can be indexed and sliced.
Difference between list and tupe
* literal
```
sometupe = 1,2
somelist = [1,3]
```
* size
```
a = tuple(range(1000))
b = list(range(1000))
a.__sizeof__() Out[69]: 8024
b.__sizeof__() Out[70]: 9088
```
Due to the smaller size of tupe operation, it becomes a bit faster, but not that much to mention about until you have a huge number
of element.

* Permitted operations
```
b    = [1,2]
b[0] = 3
a    = (1,2)
a[0] = 3 
TypeError: 'tuple' object does not support item assignment
```
That also means that you can't delete an element or sort a tuple. However, you could add new element to both list and tuple with the only difference that you will change id of the tuple by adding element
```
a     = (1,2)
b     = [1,2] 
id(a) Out[76]: 78418888
id(b) Out[77]: 85315848

a   += (3,)
b   += [3]
id(a) Out[80]: 85343616
id(b) Out[81]: 85315848
```
* Usage
As a list is mutable, it can't be used as a key in a dictionary, whereas a tuple can be used.
```
a    = (1,2)
b    = [1,2] 
c = {a: 1}
c = {b: 1} TypeError: unhashable type: 'list'
```
One example would be pairs of page and line number to reference locations in a book, e.g.:
```
my_location = (42, 11)  # page number, line number
```
You can then use this as a key in a dictionary to store notes on locations. A list on the other hand could be used to store multiple locations. Naturally one might want to add or remove locations from the list, so it makes sense that lists are mutable. On the other hand it doesn't make sense to add or remove items from an existing location - hence tuples are immutable.

## wrapper
python is a high level(highly abstracted, or English-like ) language. This abstraction comes at a prices in excution speed, and
sometimes it becomes necessary to use lower level languages to do fast computations. A wrapper is code that provides a **bridge 
between high and the low level languages**. allowing e.g. , python to excute code written in C or Fortran.

Examples include ctypes, SWIG and Cython (which wraps C and C++) and f2py (which wraps Fortran).



















