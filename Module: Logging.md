# [Logging facility for Python](https://docs.python.org/3.6/library/logging.html)
This module defines functions and classes which implement a flexible event logging system for applications and libraries.

The basic classes defined by the module, together with their functions, are listed below.
```
Loggers   : expose the interface that application code directly uses.
Handlers  : send the log records (created by loggers) to the appropriate destination.
Filters   : provide a finer grained facility for determining which log records to output.
Formatters: specify the layout of log records in the final output.
```
## Logger Objects
```
but always through the module-level function logging.getLogger(name)
logging.getLogger(__name__) recommended construction. 
That’s because in a module, __name__ is the module’s name in the Python package namespace
```
class logging.Logger
```
setLevel(level)
debug
info
warning
error
critical
exception
addHandler
```



## Logging Levels
Level	Numeric value
```
CRITICAL	50
ERROR	40
WARNING	30
INFO	20
DEBUG	10
NOTSET	0
```

## Handler Objects
logging.Handler
```
setLevel
setFormatter
addFilter
```

## Formatter Objects
class logging.Formatter(fmt=None, datefmt=None, style='%')


## Filter Objects
Filters can be used by Handlers and Loggers for more sophisticated filtering than is provided by levels. 

## LogRecord Objects
LogRecord instances are created automatically by the Logger every time something is logged, and can be created manually via makeLogRecord()

## LogRecord attributes
The LogRecord has a number of attributes, most of which are derived from the parameters to the constructor.

```
FORMAT = '[%(asctime)s] %(name)-15s %(message)s'
DATEFMT = "%H:%M:%S"
logging.basicConfig(format=FORMAT, datefmt=DATEFMT, level=logging.INFO)
```


## LoggerAdapter Objects

LoggerAdapter instances are used to conveniently pass contextual information into logging calls

## Thread Safety
The logging module is intended to be thread-safe without any special work needing to be done by its clients. It achieves this though using threading locks; there is one lock to serialize access to the module’s shared data, and each handler also creates a lock to serialize access to its underlying I/O.

##  Module-Level Functions
logging.basicConfig(**kwargs)
```
filename
filemode
format
datefmt
style
level
stream
handlers
```




## Module-Level Attributes



## Integration with the warnings module





Start with a simple example:
```
import logging

logging.basicConfig(filename='employee.log', level=logging.INFO,
                    format='%(levelname)s:%(message)s')


class Employee:
    """A sample Employee class"""

    def __init__(self, first, last):
        self.first = first
        self.last = last

        logging.info('Created Employee: {} - {}'.format(self.fullname, self.email))

    @property
    def email(self):
        return '{}.{}@email.com'.format(self.first, self.last)

    @property
    def fullname(self):
        return '{} {}'.format(self.first, self.last)


emp_1 = Employee('John', 'Smith')
emp_2 = Employee('Corey', 'Schafer')
emp_3 = Employee('Jane', 'Doe')

```
you got the information
```
INFO:Created Employee: John Smith - John.Smith@email.com
INFO:Created Employee: Corey Schafer - Corey.Schafer@email.com
INFO:Created Employee: Jane Doe - Jane.Doe@email.com
```
More advance Method:
```
import logging

logger = logging.getLogger(__name__)
logger.setLevel(logging.DEBUG)

formatter = logging.Formatter('%(asctime)s:%(name)s:%(message)s')

file_handler = logging.FileHandler('sample.log')
file_handler.setLevel(logging.DEBUG)
file_handler.setFormatter(formatter)

stream_handler = logging.StreamHandler()
stream_handler.setFormatter(formatter)

logger.addHandler(file_handler)
logger.addHandler(stream_handler)


def loger(original_function):
    def wrapper_function(num_1, num_2):
        logger.debug('{:s}: Parameters: {},{}'.format(original_function.__name__, num_1.shape, num_2.shape))
        return original_function(num_1, num_2)
    return wrapper_function

@loger
def add(x, y):
    """Add Function"""
    return x + y
def subtract(x, y):
    """Subtract Function"""
    return x - y


def multiply(x, y):
    """Multiply Function"""
    return x * y


def divide(x, y):
    """Divide Function"""
    try:
        result = x / y
    except ZeroDivisionError:
        logger.exception('Tried to divide by zero')
    else:
        return result

import numpy as np
num_1 = np.array([10, 5])
num_2 = np.array([1, 2])

add_result = add(num_1, num_2)
#logger.debug('Add: {} + {} = {}'.format(num_1, num_2, add_result))

sub_result = subtract(num_1, num_2)
logger.debug('Sub: {} - {} = {}'.format(num_1, num_2, sub_result))

mul_result = multiply(num_1, num_2)
logger.debug('Mul: {} * {} = {}'.format(num_1, num_2, mul_result))

div_result = divide(num_1, num_2)
logger.debug('Div: {} / {} = {}'.format(num_1, num_2, div_result))
```
Using the decorator can simplify the dubug code.
```
2018-01-20 10:42:03,239:__main__:add: Parameters: (2,),(2,)
2018-01-20 10:42:03,239:__main__:Sub: [10  5] - [1 2] = [9 3]
2018-01-20 10:42:03,240:__main__:Mul: [10  5] * [1 2] = [10 10]
2018-01-20 10:42:03,241:__main__:Div: [10  5] / [1 2] = [10.   2.5]
```
But there is one problem that decorator only affect front part of a function, i.e., you can look into what is put into the function.
