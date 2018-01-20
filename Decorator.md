# Decorator
an operator that transforms a function, for example, a log decorator may be defined to print debugging information  
upon function execution:
## Necessary
We can use one format to decorate many functions: so you can use it to monitor what the code snippet is going on with only one identifier.
you can debug the code easily.

## Mechanism
```
def decorator_funciton(original_function):
    Print('The information before the function,e.g., Construct the method and so on ')    
    def wrapper_function(*args, **kwargs):
        print("Logging call with parameters:", args, kwargs)
        result = original_function(*args, **kwargs)
        print("The result is what, you can talke about.") 
        return result     
    return wrapper_function
```
The decorator_function only take the function as the argument, then return a wrapperfunction. Therefore, you just put 
the latter argument pass to the original function. It doesn't pass through the decorator function, instead, the wrapper function take 
all the parameters and pass to the original function.

## Advanced method 
Look for more information:[ Here](https://www.ibm.com/developerworks/library/l-cpdecor/index.html)


## Examples
then we define a function we can decorate it using *decorator_funciton*
```
def decorator_function(orginal_function):
    def wrapper_function(one, another):
        print('The method is Called')
        result = orginal_function(one, another)
        print('{}:Parameter:{},{};Result is {}'.format(orginal_function.__name__, one, another, result))
        return result
    return wrapper_function
@decorator_function
def add(a, b):
    return a + b
@decorator_function
def mul(a, b):
    return a * b
add(1, 2)
mul(2, 4)

```
the way is equivalent to the following original way:
```
decorated_add = decorator_funciton(add)
```
Thus the result can be:
```
The method is Called
add:Parameter:1,2;Result is 3
The method is Called
mul:Parameter:2,4;Result is 8
```
