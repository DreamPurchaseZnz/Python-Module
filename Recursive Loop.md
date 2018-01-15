# [Recursive Functions](https://www.python-course.eu/recursive_functions.php)
The adjective recursive means 'to run back'. and this is what a definition or a recursive function does: it is run backing or returning 
to itself. 

## recursive function in python
```
def factorial(n):
    if n == 1:
        return 1
    else:
        return n * factorial(n-1)

``` 

we can track how the function works by adding two print() function to previous function defination
```
def factorial(n):
    print("factorial has been called with n = " + str(n))
    if n == 1:
        return 1
    else:
        res = n * factorial(n-1)
        print("intermediate result for ", n, " * factorial(" ,n-1, "): ",res)
        return res	

print(factorial(5))

```
the python script output the following result:
```
factorial has been called with n = 5
factorial has been called with n = 4
factorial has been called with n = 3
factorial has been called with n = 2
factorial has been called with n = 1
intermediate result for  2  * factorial( 1 ):  2
intermediate result for  3  * factorial( 2 ):  6
intermediate result for  4  * factorial( 3 ):  24
intermediate result for  5  * factorial( 4 ):  120
120

```
```
def iterative_factorial(n):
    result = 1
    for i in range(2,n+1):
        result *= i
    return result

```


## Fibonacci
Recursive version
```
def fib(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fib(n-1) + fib(n-2)
    
fib(12)
Out[10]: 
144
```
and iterative solution for the problem
```
def fibi(n):
    a, b = 0, 1
    for i in range(n):
        a, b = b, a + b
    return a
```
The recursive verison seems much slow as the number n grow up.
We can think 





