# [Error and Exceptions](https://docs.python.org/3/tutorial/errors.html)
There are two distinguishable kinds of errors: *syntax error* and *exceptions*
```
try                                                  # lets you test a block of code for errors.
except                                               # lets you handle the error.
finally                                              # lets you execute code, regardless of the result of 
                                                             the try- and except blocks.
```
## Skip the bad case
```
for i in range(10):
    try:
        print(x)
    except Exception as err:
        print(err)                # name 'x' is not defined
```

## Syntax Errors
Syntax Errors also known as parsing errors, are perhaps the most commom kind of complaint.
```
b(0) =1
  File "<ipython-input-19-e2a0e706ca68>", line 1
    b(0) =1
           ^
SyntaxError: can't assign to function call

```
## Exceptions
Even if a statement or expression is syntactically correct, it may cause an error when an attempt is made to execute it.
> Error detected during execution are called *Exceptions* and not conditionally fatal: you will soon learn how to handle it.
Most exceptions are not handled by programs, however, and result in error messages as shown here:
```
10 * (1/0)
Traceback (most recent call last):
  File "C:\Program Files\Anaconda3\lib\site-packages\IPython\core\interactiveshell.py", line 2881, in run_code
    exec(code_obj, self.user_global_ns, self.user_ns)
  File "<ipython-input-20-9ce172bd90a7>", line 1, in <module>
    10 * (1/0)
ZeroDivisionError: division by zero

```
## [Built-in Exceptions](https://docs.python.org/3/library/exceptions.html#bltin-exceptions)
```
Exception                       
AttributeError             
IOError                  
IndexError    
KeyError    
NameError     
SyntaxError     
TypeError           
ValueError   
ZeroDivisionError         
```

## Handling Exceptions
It is possible to write programs that handle selected exceptions. Look at the following example, which asks the user for input until a valid integer has been entered, but allows the user to interrupt the program (using Control-C or whatever the operating system supports); note that a user-generated interruption is signalled by raising the KeyboardInterrupt exception.
```
>>> def this_fails():
...     x = 1/0
...
>>> try:
...     this_fails()
... except ZeroDivisionError as err:
...     print('Handling run-time error:', err)
...
Handling run-time error: division by zero
```
## Raising Exceptions

The raise statement allows the programmer to force a specified exception to occur. For example
```
raise NameError('HiThere')
Traceback (most recent call last):
  File "C:\Program Files\Anaconda3\lib\site-packages\IPython\core\interactiveshell.py", line 2881, in run_code
    exec(code_obj, self.user_global_ns, self.user_ns)
  File "<ipython-input-21-93385ba972b1>", line 1, in <module>
    raise NameError('HiThere')
NameError: HiThere
```
If you need to determine whether an exception was raised but don’t intend to handle it, a simpler form of the raise statement allows you to re-raise the exception:
```
try:
...     raise NameError('HiThere')
... except NameError:
...     print('An exception flew by!')
...     raise
Traceback (most recent call last):
  File "C:\Program Files\Anaconda3\lib\site-packages\IPython\core\interactiveshell.py", line 2881, in run_code
    exec(code_obj, self.user_global_ns, self.user_ns)
  File "<ipython-input-22-3f47609917d7>", line 2, in <module>
    raise NameError('HiThere')
NameError: HiThere
An exception flew by!
```
##  User-defined Exceptions
Programs may name their own exceptions by creating a new exception class (see Classes for more about Python classes). Exceptions should typically be derived from the Exception class, either directly or indirectly.
```
class Error(Exception):
    """Base class for exceptions in this module."""
    pass
    
class InputError(Error):
    """Exception raised for errors in the input.

    Attributes:
        expression -- input expression in which the error occurred
        message -- explanation of the error
    """

    def __init__(self, expression, message):
        self.expression = expression
        self.message = message


```
## Defining Clean-up Actions

The try statement has another optional clause which is intended to define clean-up actions that must be executed under all circumstances. For example:
```
>>> try:
...     raise KeyboardInterrupt
... finally:
...     print('Goodbye, world!')
Traceback (most recent call last):
  File "C:\Program Files\Anaconda3\lib\site-packages\IPython\core\interactiveshell.py", line 2881, in run_code
    exec(code_obj, self.user_global_ns, self.user_ns)
  File "<ipython-input-23-ee01f6bed4b3>", line 2, in <module>
    raise KeyboardInterrupt
KeyboardInterrupt
Goodbye, world!
```
A finally clause is always executed before leaving the try statement, whether an exception has occurred or not. When an exception has occurred in the try clause and has not been handled by an except clause (or it has occurred in an except or else clause), it is re-raised after the finally clause has been executed. The finally clause is also executed “on the way out” when any other clause of the try statement is left via a break, continue or return statement. A more complicated example:
```
def divide(x, y):
...     try:
...         result = x / y
...     except ZeroDivisionError:
...         print("division by zero!")
...     else:
...         print("result is", result)
...     finally:
...         print("executing finally clause")
divide(2, 1)
result is 2.0
executing finally clause
divide(2, 0)
division by zero!
executing finally clause

divide("2", "1")
Traceback (most recent call last):
executing finally clause
  File "C:\Program Files\Anaconda3\lib\site-packages\IPython\core\interactiveshell.py", line 2881, in run_code
    exec(code_obj, self.user_global_ns, self.user_ns)
  File "<ipython-input-27-62cca4a1982f>", line 1, in <module>
    divide("2", "1")
  File "<ipython-input-24-51d87ebac009>", line 3, in divide
    result = x / y
TypeError: unsupported operand type(s) for /: 'str' and 'str'

```

## Predefined Clean-up Actions



