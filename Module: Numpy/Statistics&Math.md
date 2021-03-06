# [Math](https://docs.scipy.org/doc/numpy/reference/routines.math.html)

The follow operation is element-wise unless otherwise specified

## Trigonometric functions
```

sin(x, /[, out, where, casting, order, ...])
cos(x, /[, out, where, casting, order, ...])
tan(x, /[, out, where, casting, order, ...])
arcsin(x, /[, out, where, casting, order, ...])
arccos(x, /[, out, where, casting, order, ...])
arctan(x, /[, out, where, casting, order, ...])
hypot(x1, x2, /[, out, where, casting, ...])
arctan2(x1, x2, /[, out, where, casting, ...])
degrees(x, /[, out, where, casting, order, ...])
radians(x, /[, out, where, casting, order, ...])
unwrap(p[, discont, axis])
deg2rad(x, /[, out, where, casting, order, ...])
rad2deg(x, /[, out, where, casting, order, ...])
```
## Hyperbolic functions

## rounding
```

around(a[, decimals, out])
round_(a[, decimals, out])
rint(x, /[, out, where, casting, order, ...])
fix(x[, out])
floor(x, /[, out, where, casting, order, ...])
ceil(x, /[, out, where, casting, order, ...])
trunc(x, /[, out, where, casting, order, ...])
```
## Sums, products, differences
```
prod(a[, axis, dtype, out, keepdims]) 
sum(a[, axis, dtype, out, keepdims]) 
nanprod(a[, axis, dtype, out, keepdims]) 
nansum(a[, axis, dtype, out, keepdims]) 
cumprod(a[, axis, dtype, out]) 
cumsum(a[, axis, dtype, out]) 
nancumprod(a[, axis, dtype, out]) 
nancumsum(a[, axis, dtype, out]) 
diff(a[, n, axis]) 
ediff1d(ary[, to_end, to_begin]) 
gradient(f, *varargs, **kwargs) 
cross(a, b[, axisa, axisb, axisc, axis]) 
trapz(y[, x, dx, axis]) 
```
## Exponents and logarithms

## Other special functions

## Floating point routines

## Arithmetic operations

## Handling complex numbers

## Miscellaneous

# Statistics
## [Order statistics](https://docs.scipy.org/doc/numpy-1.13.0/reference/routines.statistics.html)
```
amin(a[, axis, out, keepdims])
amax(a[, axis, out, keepdims])
nanmin(a[, axis, out, keepdims])
nanmax(a[, axis, out, keepdims])
ptp(a[, axis, out])
percentile(a, q[, axis, out, ...])
nanpercentile(a, q[, axis, out, ...])
```
## Averages and variances
```
median(a[, axis, out, overwrite_input, keepdims])
average(a[, axis, weights, returned])
mean(a[, axis, dtype, out, keepdims])
std(a[, axis, dtype, out, ddof, keepdims])
var(a[, axis, dtype, out, ddof, keepdims])
nanmedian(a[, axis, out, overwrite_input, ...])
nanmean(a[, axis, dtype, out, keepdims])
nanstd(a[, axis, dtype, out, ddof, keepdims])
nanvar(a[, axis, dtype, out, ddof, keepdims])

```
## Correlating
```
corrcoef(x[, y, rowvar, bias, ddof])
correlate(a, v[, mode])
cov(m[, y, rowvar, bias, ddof, fweights, ...])
```
## Histograms
```

histogram(a[, bins, range, normed, weights, ...])
histogram2d(x, y[, bins, range, normed, weights])
histogramdd(sample[, bins, range, normed, ...])
bincount(x[, weights, minlength])
digitize(x, bins[, right])
```

# [The N-dimensional array](https://docs.scipy.org/doc/numpy-1.13.0/reference/arrays.ndarray.html)
## Array attributes
[Attributes](https://docs.scipy.org/doc/numpy/reference/generated/numpy.chararray.html)
```
ndarray.T
```

```
T                                       ---> Self.transpose()
dtype                                   ---> Data type
flat                                    ---> 1-D array 
ndim                                    ---> Number of demension
real                                    ---> Real part of the array
shape                                   ---> Tupe of array dimensions
size                                    ---> Number of elements in array

# other attributes
base
ctype
data
flags
imag
itemsize
nbytes
stride
``` 
Assign the exact position a value, we can do like this:
```
c = np.zeros((4,3))
c[[0,1,2,3],[2,1,1,0]] = [1,1,1,1]
c
Out[10]: 
array([[ 0.,  0.,  1.],
       [ 0.,  1.,  0.],
       [ 0.,  1.,  0.],
       [ 1.,  0.,  0.]])


```



Methods
```
astype                                   ---> Copy of the array ,cast to a specified type
copy([order])      
count(sub[, start, end])          
decode([encoding, errors])           
dump(file)          
dumps()           
encode([encoding, errors])           
endswith(suffix[, start, end])           
expandtabs([tabsize])           
fill(value)                              ---> Fill the array with a scalar value.
find(sub[, start, end])                  ---> For each element
flatten([order])                         ---> Return a copy of the array collapsed into one dimension.
getfield(dtype[, offset])           
index(sub[, start, end])           
isalnum()                                ---> Returns true for each element if all characters in the string are alphanumeric 
isalpha()          
isdecimal()           
isdigit()           
islower()           
isnumeric()          
isspace()           
istitle()           
isupper()           
item(*args)           
join(seq)           
ljust(width[, fillchar])          
lower()                                 ---> Return an array with the elements of self converted to lowercase.
lstrip([chars])           
nonzero()                               ---> Return the indices of the elements that are non-zero.
put(indices, values[, mode])            ---> Set a.flat[n] = values[n] for all n in indices.
ravel([order])          
repeat(repeats[, axis])                 ---> Repeat elements of an array.
replace(old, new[, count])              ---> return a copy of the string with all occurrences of substring old replaced by new.
reshape(shape[, order])                 ---> Returns an array containing the same data with a new shape.
resize(new_shape[, refcheck])           ---> Change shape and size of array in-place.
rfind(sub[, start, end])                ---> For each element in self, return the highest index in the string 
rindex(sub[, start, end])               ---> Like rfind, but raises ValueError when the substring sub is not found.
rjust(width[, fillchar])           
rsplit([sep, maxsplit])          
rstrip([chars])           
searchsorted(v[, side, sorter])           
setfield(val, dtype[, offset])          
setflags([write, align, uic])           
sort([axis, kind, order])              ---> Sort an array, in-place.
split([sep, maxsplit])           
splitlines([keepends])           
squeeze([axis])         
startswith(prefix[, start, end])           
strip([chars])           
swapaxes(axis1, axis2)           
swapcase()           
take(indices[, axis, out, mode])          
title()          
tofile(fid[, sep, format])           
tolist()           
tostring([order])           
translate(table[, deletechars])           
transpose(*axes)                      ---> Returns a view of the array with axes transposed.
upper()           
view([dtype, type])          
zfill(width)                         ---> Return the numeric string left-filled with zeros in a string of length width.
```






