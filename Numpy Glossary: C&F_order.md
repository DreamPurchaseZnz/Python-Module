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
## array_like

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

## decorator











