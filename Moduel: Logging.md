# [Logging facility for Python](https://docs.python.org/3.6/library/logging.html)
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
## Logger Objects


## Logging Levels

## Handler Objects


## Formatter Objects

## Filter Objects

## LogRecord Objects


## LogRecord attributes


## LoggerAdapter Objects


## Thread Safety


##  Module-Level Functions



## Module-Level Attributes



## Integration with the warnings module





