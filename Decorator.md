# decorator
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

## Examples
then we define a function we can decorate it using *decorator_funciton*
```
@decorator_funciton
def add(a, b):
    return a + b
```
the way is equivalent to the following original way:
```
decorated_add = decorator_funciton(add)
```
Thus the result can be:
```
add(1,2)
Logging call with parameters: (1, 2) {}
Out[12]: 
3
```
```
decorated_add(1, 2)
Logging call with parameters: (1, 2) {} # first time decorate by @ operator
Logging call with parameters: (1, 2) {}              
Out[14]: 
3
```
