Array Creation Routines
---------------------------------------------------------------------------------------------------
## Ones and zeros
```
empty                                          ---> Without initializing entries.
empty_like                                     ---> The same shape and type as a given array.
eye                                            ---> Return a 2-D array with ones on the diagonal and zeros elsewhere.
identity                                       ---> Return a square array with ones on the main diagonal                             ones                                           ---> Return a new array of given shape and type, filled with ones.
ones_like                                      ---> Return an array of ones with the same shape and type as a given array.
zeros                                          ---> Return a new array of given shape and type, filled with zeros.
zeros_like                                     ---> Return an array of zeros with the same shape and type as a given array.
full                                           ---> Return a new array of given shape and type, filled with fill_value.
full_like                                      ---> Return a full array with the same shape and type as a given array.
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
## Building matrices
```
diag                                           ---> Extract a diagonal or construct a diagonal array.
diagflat                                       ---> Create a two-dimensional array with the flattened input as a diagonal.
tri                                            ---> An array with ones at and below the given diagonal and zeros elsewhere.
tril                                           ---> Lower triangle of an array.
triu                                           ---> Upper triangle of an array.
vander
```
## The Matrix class
```
mat
bmat
```


## From existing data
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
## Creating record arrays
```
core.records.array
core.records.fromarrays
core.records.fromrecords
core.records.fromstring
core.records.fromfile
```



