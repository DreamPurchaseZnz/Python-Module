# Lambda, filter, reduce and map
## Lambda Operator
If Guido van Rossum, the author of the programming language python, had got his will, the Lambda operator will be elluminated.
the lambda function can be written as following:
```
lambda list of arguments: expression
```
The argument list consists of a comma sperated list of arguments and an expression is an arithmetic expression using the argments. 
you can alse assign the function to a variable to give it a name.
The following example of a lambda function returns the sum of its two argments
```
sum = lambda x,y: x+y
sum(2,3)
Out[77]: 
5
```
## the map() function
map() is a function which takes two argments
```
r = map(func, seqence)
map(function_to_apply, list_of_inputs)
```
The first argment *func* is  a function and the second a sequence. 
map() applies the function *func* to all the elements of the sequence *seq*. Before python3 , map() used to return a list, which each 
element of the result list was the result of the function *func* applied on each corresponding element of the list or tupe"seq".
In python 3, map() return a iterator,thus need a *list* function to show what is in the interator.

The following example illustrates the way of working of map():
```
a = [1,2,3,4]
b = [1,3,5,7]
list(map(lambda x,y: x+y, a,b))
Out[85]: 
[2, 5, 8, 11]
```
That is:
```
map(function_to_apply, list_of_inputs)
```
```
items = [1, 2, 3, 4, 5]
squared = []
for i in items:                       # pass all the list elements to a function one-by-one
    squared.append(i**2)              #  then collect the output
```
Map allows us to implement this in a much simpler and nicer way. Here you go:
```
items = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, items))
```

```
def multiply(x):                   #Instead of a list of inputs 
    return (x*x)
def add(x):                        # we can even have a list of functions!
    return (x+x)

funcs = [multiply, add]
for i in range(5):
    value = list(map(lambda x: x(i), funcs))
    print(value)

# Output:
# [0, 0]
# [1, 2]
# [4, 4]
# [9, 6]
# [16, 8]
```


## Mapping a list of functions
we can write a function which applies a branch of functions, which may be an iterable
```
from math import sin, cos, tan, pi
def map_functions(x, functions):
     """ map an iterable of functions on the the object x """
     res = []
     for func in functions:
         res.append(func(x))
     return res
     
# test the result
family_of_functions = (sin, cos, tan)
print(map_functions(pi, family_of_functions))

[1.2246467991473532e-16, -1.0, -1.2246467991473532e-16]
```
The previously defined map_functions function can be simplified with the list comprehension technique, which we will cover in the chapter list comprehension:
```
def map_functions(x, functions):
     return [ func(x) for func in functions ]
```
## filter 
the function
```
filter(function, sequence)

```
offer an elegant way to filter out all the elements of a sequence.
The function filter need a function f as its first argment. **f has to return a Boolean value**, i.e. either True or False. This function will be applied to every element of sequence.

```
>>> fibonacci = [0,1,1,2,3,5,8,13,21,34,55]
>>> odd_numbers = list(filter(lambda x: x % 2, fibonacci))
>>> print(odd_numbers)
[1, 1, 3, 5, 13, 21, 55]
>>> even_numbers = list(filter(lambda x: x % 2 == 0, fibonacci))
>>> print(even_numbers)
[0, 2, 8, 34]
```

## Reducing a list
the function reduce has been dropped from the core of python when migrating to python3

Reduce is a really useful function for performing some computation on a list and returning the result.

It applies **a rolling computation** to sequential pairs of values in a list. For example, if you wanted to compute the product of a list of integers.
```
reduce(func, seq)
```
It will return a single value, rather than the sequence seq.

If seq = \[s1,s2,...,sn\], calling reduce(function, sequence) work like this:

```
      s1, s2, s3, s4, ..., sn
1.func(s1,s2)
    2. func(func(s1,s2),s3)
      3. ....
```

So the normal way you might go about doing this task in python is using a basic for loop:
```
product = 1
list = [1, 2, 3, 4]
for num in list:
    product = product * num

# product = 24
```
Now let’s try it with reduce:
```
from functools import reduce
product = reduce((lambda x, y: x * y), [1, 2, 3, 4])

# Output: 24
```
If we want to use the reduce function, we have to import functools to be capable of using reduce.
```
>>> import functools
>>> functools.reduce(lambda x,y: x+y, [47,11,42,13])
113
>>> 
```
# [List Comprehension](https://www.python-course.eu/python3_list_comprehension.php)
The father of python Guido van Rossum prefers list comprehensions to constructs using map, filter,reduce and lambda. 
This chapter we will cover the essentials about list comprehensions.

List Comprehensions is in python'way of implementing a well known notation for sets as used by mathematicians.
e.g., the square number of the natural numbers are for example created by {x^2|x \in \mathbb N}

## Examples:
In the List Comprehension way, the lambda and map() can be defined as following
```
>>> Celsius = [39.2, 36.5, 37.3, 37.8]
>>> Fahrenheit = [ ((float(9)/5)*x + 32) for x in Celsius ]
>>> print(Fahrenheit)
[102.56, 97.700000000000003, 99.140000000000001, 100.03999999999999]
>>> 
```
A pythegorean triple consists of three positive integers a, b and c.
```
[(x,y,z) for x in range(1, 30) for y in range(x,30) for z in range(y,30) if x**2 +y**2 == z**2]
Out[91]: 
[(3, 4, 5),
 (5, 12, 13),
 (6, 8, 10),
 (7, 24, 25),
 (8, 15, 17),
```

Let A and B be two sets, the cross product of A and B ,written AxB 
```
>>> colours = [ "red", "green", "yellow", "blue" ]
>>> things = [ "house", "car", "tree" ]
>>> coloured_things = [ (x,y) for x in colours for y in things ]
>>> print(coloured_things)
[('red', 'house'), ('red', 'car'), ('red', 'tree'), ('green', 'house'), ('green', 'car'), ('green', 'tree'), ('yellow', 'house'), ('yellow', 'car'), ('yellow', 'tree'), ('blue', 'house'), ('blue', 'car'), ('blue', 'tree')]
>>> 
```
## Generator Comprehension
Generator comprehensions were introduced with Python 2.6. They are simply like a list comprehension but with parentheses - round brackets - instead of (square) brackets around it. Otherwise, the syntax and the way of working is like list comprehension, but a generator comprehension returns a generator instead of a list.
```
x = (x **2 for x in range(20))
x
Out[93]: 
<generator object <genexpr> at 0x000000000BDA97D8>
list(x)

```
## Set Comprehension
A set comprehension is similar to a list comprehension, but returns a set and not a list. Syntactically, we use curly brackets instead of square brackets to create a set. Set comprehension is the right functionality to solve our problem from the previous subsection. We are able to create the set of non primes without doublets:
```
>>> from math import sqrt
>>> n = 100
>>> sqrt_n = int(sqrt(n))
>>> no_primes = {j for i in range(2,sqrt_n) for j in range(i*2, n, i)}
>>> no_primes
{4, 6, 8, 9, 10, 12, 14, 15, 16, 18, 20, 21, 22, 24, 25, 26, 27, 28, 30, 32, 33, 34, 35, 36, 38, 39, 40, 42, 44, 45, 46, 48, 49, 50, 51, 52, 54, 55, 56, 57, 58, 60, 62, 63, 64, 65, 66, 68, 69, 70, 72, 74, 75, 76, 77, 78, 80, 81, 82, 84, 85, 86, 87, 88, 90, 91, 92, 93, 94, 95, 96, 98, 99}
>>> primes = {i for i in range(n) if i not in no_primes}
>>> print(primes)
{0, 1, 2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97}
>>> 
```









