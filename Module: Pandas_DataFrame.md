# Module: Pandas.DataFrame
----------------------------------------------------------------------------------------------------------------
Two-dimensional size-mutable, potentially heterogenious tabular data structure with labeled axes(rows and columns)
Arithmetic operation align on both row and column lables ,can be thought of dict_like container for series objects
The primary pandas data structure.
```
class pandas.DataFrame(data=None, index=None, columns=None, dtype=None, copy=False)
```
```
data                               ---> Numpy ndarray (structured or homogeneous), dict, or DataFrame
                                        Dict can contain Series, arrays, constants, or list-like objects
index                              ---> Row index, default to np.arange(n)
columns                            ---> Columns index
dtype                              ---> Data type to force otherwise infer
copy                               ---> Boolean ,default False
```

**Attributes**
```
T                                  ---> Transpose index and columns
at              
axes                               ---> Return a list with the row axis labels and column axis labels as the only members.
blocks              
dtypes              
empty              
ftypes              
iat              
iloc              
is_copy              
ix              
loc              
ndim                              ---> Number of axes / array dimensions
shape                             ---> Return a tuple representing the dimensionality of the DataFrame.
size                              ---> Number of elements in the NDFrame
style              
values              
```
