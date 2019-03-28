# Broadcasting
Term broadcasting descrides how numpy treats arrays with different shapes during arithmetic operation.
Subject to certain constraint, the *smaller* array is "broadcasting" across the larger array so that they have compatible shapes.

The simplest broadcasting example occurs in an operation like the following
```
>>> a = np.array([1.0, 2.0, 3.0])
>>> b = 2.0
>>> a * b
array([ 2.,  4.,  6.])
```
We can think of a scalar **b**  being streched during the arithmetic operation into an array with the same shape of **a**

## General Broadcasting Rules
when operating on two arrays, Numpy compare their shapes element-wise, It starts with the trailing dimensions and work it forward
Two dimensions are compatible when
```
1. they are equal
2. one of them is 1
```
If these conditions are not met, *a valueError: frames are not aligned* exception is thrown.

the output array is the maximum size along each dimension of the input arrays
Right:
```
Image  (3d array): 256 x 256 x 3
Scale  (1d array):             3
Result (3d array): 256 x 256 x 3
```
False:
```
Image  (3d array): 3 x 256 x 256
Scale  (1d array):             3
Result (3d array): 3 x 256 x 256
```

More examples:
```
A      (4d array):  8 x 1 x 6 x 1
B      (3d array):      7 x 1 x 5
Result (4d array):  8 x 7 x 6 x 5

A      (2d array):  5 x 4
B      (1d array):      1
Result (2d array):  5 x 4

A      (2d array):  5 x 4
B      (1d array):      4
Result (2d array):  5 x 4

A      (3d array):  15 x 3 x 5
B      (3d array):  15 x 1 x 5
Result (3d array):  15 x 3 x 5

A      (3d array):  15 x 3 x 5
B      (2d array):       3 x 5
Result (3d array):  15 x 3 x 5

A      (3d array):  15 x 3 x 5
B      (2d array):       3 x 1
Result (3d array):  15 x 3 x 5

```
Here are examples of shapes that do not broadcast:
```
A      (1d array):  3
B      (1d array):  4 # trailing dimensions do not match

A      (2d array):      2 x 1
B      (3d array):  8 x 4 x 3 # second from last dimensions mismatched
```


An example of broadcasting in practice:
```
x = np.arange(4)
x
Out[123]: 
array([0, 1, 2, 3])
xx = x.reshape(4,1)
y = np.ones(5)
z = np.ones((3,4))
y
Out[127]: 
array([ 1.,  1.,  1.,  1.,  1.])
z
Out[128]: 
array([[ 1.,  1.,  1.,  1.],
       [ 1.,  1.,  1.,  1.],
       [ 1.,  1.,  1.,  1.]])
x + y
Traceback (most recent call last):
  File "C:\Program Files\Anaconda3\lib\site-packages\IPython\core\interactiveshell.py", line 2881, in run_code
    exec(code_obj, self.user_global_ns, self.user_ns)
  File "<ipython-input-129-b50c5120e24b>", line 1, in <module>
    x + y
ValueError: operands could not be broadcast together with shapes (4,) (5,) 
(xx + y).shape
Out[130]: 
(4, 5)
xx + y                                           ---> similar to meshgrid operation
Out[131]: 
array([[ 1.,  1.,  1.,  1.,  1.],
       [ 2.,  2.,  2.,  2.,  2.],
       [ 3.,  3.,  3.,  3.,  3.],
       [ 4.,  4.,  4.,  4.,  4.]])
x + z
Out[132]: 
array([[ 1.,  2.,  3.,  4.],
       [ 1.,  2.,  3.,  4.],
       [ 1.,  2.,  3.,  4.]])
(x+z).shape
Out[133]: 
(3, 4)





```



