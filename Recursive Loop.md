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
We can cousider the recursive version as a calculation tree, and the subtrees f(n-1).. will be called many times. This means recursive version doesn't remember previouly values.

so we can implement a 'memory' for our recursive version by using a dictionary to save the previously calculated values.
```
memo = {0:0, 1:1}
def fibm(n):
    if not n in memo:
        memo[n] = fibm(n-1) + fibm(n-2)
    return memo[n]
```
## advantage of recursion  
* recursive functions make the code look clean and elegant
* A complex task can be broken down into simpler sub-problem using recursion
* sequence generation is easier with recursion that using some nested iteration

## disadvantages of recursion
* Sometimes the logic behind recursion is hard to follow through.
* Recursive calls are expensive (inefficient) as they take up a lot of memory and time.
* Recursive functions are hard to debug.


## Recursion in with a list
adding all numbers in a list.  Without recursion, this could be:
```
def sum(list):
    sum = 0
 
    # Add every number in the list.
    for i in range(0, len(list)):
        sum = sum + list[i]
 
    # Return the sum.
    return sum
 
print(sum([5,7,3,8,10]))
```

the function adds every element to the variable sum and returns.  To do this recursively
```
def sum(list):
   if len(list) == 1:
        return list[0]
   else:
        return list[0] + sum(list[1:])
 
print(sum([5,7,3,8,10]))

```








