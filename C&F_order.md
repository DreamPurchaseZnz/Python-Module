numpy C order与 Fortran order 的区别
===================================
# reduction_indices
```
0  ---> get row vector by operate along column 
1  ---> get column vector
```
Fortran Order（即Row-major order）下每列在内存中是连续的，这种结构相对更加Cache-friendly。
这并不是编程语言自身的特性，在C语言中完全可以使用Column-major order，只不过访问起来计算index不太习惯而已。
Fortran大概是因为主要用于科学计算，Column-major order对于一些矩阵运算有性能优势
```
C order即Column-major order 
Fortran order即Row major order
```
Numpy默认是C order, Matlab是 Fortran order.
Most important point:  对于多维数组的Reshape，合并的计算方式是从最后一个维度开始，将最后一个维度与前一维度组成二维数组
然后采用row major order 方式将每行填入所需要结构中，从而形成一个新的维度，将这个新的维度与再之前的维度组成二维数组...以此类推，完成整个Reshape过程




numpy.reshape(a, newshape, order='C')[source]
Gives a new shape to an array without changing its data.

Parameters:	
```
a : array_like
Array to be reshaped.
newshape : int or tuple of ints
```
The new shape should be compatible with the original shape. If an integer, 
then the result will be a 1-D array of that length. One shape dimension can be -1. 
In this case, the value is inferred from the length of the array and remaining dimensions.

```
order : {‘C’, ‘F’, ‘A’}, optional
Read the elements of a using this index order, 
and place the elements into the reshaped array using this index order. 
‘C’ means to read / write the elements using C-like index order, with the last axis index changing fastest,
back to the first axis index changing slowest. ‘F’ means to read / write the elements using Fortran-like index order,
with the first index changing fastest, and the last index changing slowest.
Note that the ‘C’ and ‘F’ options take no account of the memory layout of the underlying array, 
and only refer to the order of indexing. ‘A’ means to read / write the elements in Fortran-like index order 
if a is Fortran contiguous in memory, C-like order otherwise.
```
Returns:	
```
reshaped_array : ndarray
This will be a new view object if possible; otherwise, it will be a copy. 
Note there is no guarantee of the memory layout (C- or Fortran- contiguous) of the returned array.
```
