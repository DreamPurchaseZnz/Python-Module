Array Creation Routines
---------------------------------------------------------------------------------------------------
### Ones and zeros
```
empty                                          ---> Without initializing entries
empty_like                                     ---> The same shape and type as a given array
eye                                            ---> Diagonal and zeros elsewhere.
identity                                       ---> Square array with ones on the main diagonal                             

# commonly used
ones                                           ---> Filled with ones.
zeros                                          ---> Filled with zeros.
full                                           ---> Filled with fill_value

zeros_like                                     ---> The same shape and type as a given array.
ones_like                                      ---> The same shape and type as a given array.
full_like                                      ---> The same shape and type as a given array.
```
## Numerical ranges
```
arange                                         ---> Return evenly spaced values within a given interval.
linspace                                       ---> Return evenly spaced numbers over a specified interval.
logspace                                       ---> Return numbers spaced evenly on a log scale.
geomspace                                      
meshgrid                                       ---> Return coordinate matrices from coordinate vectors.
mgrid                                          
ogrid                                          
```
### Building matrices
```
diag                                           ---> Extract a diagonal or construct a diagonal array.
diagflat                                       ---> Create a two-dimensional array with the flattened input as a diagonal.
tri                                            ---> An array with ones at and below the given diagonal and zeros elsewhere.
tril                                           ---> Lower triangle of an array.
triu                                           ---> Upper triangle of an array.
vander
```
### The Matrix class
```
mat
bmat
```


### From existing data
```
array                                          ---> Create an array.
asarray                                        ---> Convert the input to an array.
asanyarray
ascontiguousarray
asmatrix
copy
frombuffer
fromfile
fromfunctio
fromiter
fromstring
loadtxt
```
### Creating record arrays
```
core.records.array
core.records.fromarrays
core.records.fromrecords
core.records.fromstring
core.records.fromfile
```



















# Array manipulation routines
----------------------------------------------------------------------------------------------
### Basic operations
```
copyto
```
### Changing array shape
```
reshape                                        ---> Gives a new shape to an array 
ravel                                          ---> Flatten array according to order C/F 
ndarray.flat                                   ---> Flatten array according to order C
ndarray.flatten                                ---> Flatten array according to order C/F                     
```
### Transpose-like operations
```
moveaxis                                       ---> Permute
rollaxis  
swapaxes                                       ---> Interchange two axes of an array. 
ndarray.T                                      ---> Transpose  
transpose                                      ---> Permute the dimensions of an array. 
```
```
>>> x = np.array([[1,2,3]])
>>> np.swapaxes(x,0,1)
array([[1],
       [2],
       [3]])
```

### Changing number of dimension
```
atleast_1d
atleast_2d                                     ---> View inputs as arrays with at least two dimensions. 
atleast_3d                                     
broadcast  
broadcast_to 
broadcast_arrays

expand_dims                                    ---> Insert a new axis that will appear at the axis pos 
squeeze                                        ---> Remove single dimensional axis
```
[slicing](https://docs.scipy.org/doc/numpy/reference/arrays.indexing.html)
```
The newaxis object can be used in all slicing operations to create an axis of length one.
newaxis is an alias for ‘None’, and ‘None’ can be used in place of this with the same result.
```
```
In [154]: labels=np.array([1,3,5])

In [155]: labels[:,None]
Out[155]: 
array([[1],
       [3],
       [5]])

In [157]: np.arange(8)==labels[:,None]
Out[157]: 
array([[False,  True, False, False, False, False, False, False],
       [False, False, False,  True, False, False, False, False],
       [False, False, False, False, False,  True, False, False]], dtype=bool)

In [158]: (np.arange(8)==labels[:,None]).astype(int)
Out[158]: 
array([[0, 1, 0, 0, 0, 0, 0, 0],
       [0, 0, 0, 1, 0, 0, 0, 0],
       [0, 0, 0, 0, 0, 1, 0, 0]])


```
### Changing kind of array
```
asarray                                        ---> Convert the input to an array. 
asanyarray
asmatrix                                       ---> Convert the input to a matrix
asfarray                                       ---> Float array 
asfortranarray                                 ---> F order  
ascontiguousarray                              ---> Contiguous array in memory 
asarray_chkfinite 
asscalar 
require                                        ---> Satisfies requirements. 
```
### Jointing arrays
```
concatenate                                    ---> Join a sequence  of arrays along an existing axis
stack                                          ---> Join along a new axis 
column_stack                                   ---> 1D-2D by columns
dstack                                         ---> 2D-3D by third  axis-deepth
hstack                                         ---> 1D-2D by second axis-columns
vstack                                         ---> 1D-2D by first  axis-rows
block                                          ---> Block matrix
```
### Splitting arrays
```
split                                          ---> Split an array into multiple sub-arrays. 
array_split                                    ---> Same,but allow that does not equally divide the axis
dsplit                                         ---> Along the 3rd axis (depth)
hsplit                                         ---> Horizontally (column-wise)
vsplit                                         ---> Vertically (row-wise). 
```
### Tiling arrays
```
tile                                           ---> Repeating A the number of times given by reps. 
repeat                                         ---> Repeating element of array
```

### Adding and removing elements
```
delete                                         ---> Along an axis deleted. 
insert                                         ---> Insert values along the given axis before the given indices. 
append                                         ---> Append values to the end of an array. 
resize                                         ---> Resize to a new shape 
trim_zeros                                     ---> Trim the leading and/or trailing zeros from a 1-D array or sequence. 
unique                                         ---> Find the unique elements and list
```
### Rearranging elements
```
flip                                           ---> Reverse the order of elements in an array along the given axis. 
fliplr                                         ---> Flip array in the left/right direction. 
flipud                                         ---> Flip array in the up/down direction. 
reshape                                        ---> Gives a new shape to an array without changing its data. 
roll                                           ---> Roll array elements along a given axis. 
rot90                                          ---> Rotation the plane
```

