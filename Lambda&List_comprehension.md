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


