# Magic Method -Special method names
## Necessary
**For Python** A class can implement certain operations that are invoked by special syntax (such as arithmetic operations or subscripting and slicing) by defining methods with special names. This is Python’s approach to operator *overloading*

[Part of Data Model Section (More Information)](https://docs.python.org/3/reference/datamodel.html#special-method-names)


## Mechanism
The so-called magic methods have nothing to do with wizard. They are the methods with this clumsy syntax, i.e. the double underscores at the beginning and the end.  

We had used the plus sign to add numerical values, to concatenate strings or to combine lists:
```
4 + 5  # 9
'a' + 'b'  # 'ab'

int.__add__(4, 5)        # 9   
str.__add__('a', 'b')    # 'ab'
```
It's even possible to *overload* the "+" operator as well as all the other operators for the purposes of *your own class*
```
class Employee:

    raise_amt = 1.04
    
    def __init__(self, first, last, pay):
        self.first = first
        self.last = last
        self.email = first + '.' + last + '@email.com'
        self.pay = pay

    def fullname(self):
        return '{} {}'.format(self.first, self.last)

    def apply_raise(self):
        self.pay = int(self.pay * self.raise_amt)

    def __repr__(self):
        return "Employee('{}', '{}', {})".format(self.first, self.last, self.pay)

    def __str__(self):
        return '{} - {}'.format(self.fullname(), self.email)

    def __add__(self, other):
        return self.pay + other.pay

    def __len__(self):
        return len(self.fullname())


emp_1 = Employee('Corey', 'Schafer', 50000)
emp_2 = Employee('Test', 'Employee', 60000)

# print(emp_1 + emp_2)  #  110000

print(len(emp_1)) # 13
```
The mechanism works like this: If we have an expression "x + y" and x is an instance of class Employee, then Python will check the class definition of Employee. If Employee has a method \__add\__ it will be called with x.\__add\__(y), otherwise we will get an error message. 
So it is as same as the first example. the number 4 and 5 is the instance(object) of class int, so Python will check the class int definiation and get the method \__add\__.   

## Overview of Magic Methods
```
Operator Method
+   |object.__add__(self, other)
-   |object.__sub__(self, other)
*   |object.__mul__(self, other)
//  |object.__floordiv__(self, other)
/   |object.__truediv__(self, other)
%   |object.__mod__(self, other)
**  |object.__pow__(self, other[, modulo])
<<  |object.__lshift__(self, other)
>>  |object.__rshift__(self, other)
&   |object.__and__(self, other)
^   |object.__xor__(self, other)
|   |object.__or__(self, other)
```
## Extended Assignments
```
Operator	Method
+=	object.__iadd__(self, other)
-=	object.__isub__(self, other)
*=	object.__imul__(self, other)
/=	object.__idiv__(self, other)
//=	object.__ifloordiv__(self, other)
%=	object.__imod__(self, other)
**=	object.__ipow__(self, other[, modulo])
<<=	object.__ilshift__(self, other)
>>=	object.__irshift__(self, other)
&=	object.__iand__(self, other)
^=	object.__ixor__(self, other)
|=	object.__ior__(self, other)
```

## Unary Operators
```
Operator   Method
-        object.__neg__(self)
+        object.__pos__(self)
abs()    object.__abs__(self)
~        object.__invert__(self)
complex  object.__complex__(self)
int()    object.__int__(self)
long()   object.__long__(self)
float()  object.__float__(self)
oct()    object.__oct__(self)
hex()    object.__hex__(self
```
## Comparison Operators
```
Operator	Method
<   object.__lt__(self, other)
<=  object.__le__(self, other)
==  object.__eq__(self, other)
!=  object.__ne__(self, other)
>=  object.__ge__(self, other)
>   object.__gt__(self, other)
```

## other method

### object.__call__(self[, args...])
Implementing the \__call\__ magic method in a class causes its instances to become callables -- in other words, those instances now behave like functions

```
class CallMethod(object):
    def __call__(self, *args, **kwargs):
        print(args)
        print(kwargs)
    def show(self,word):
        print(word)
c = CallMethod()
isinstance(c, CallMethod)      # True
```
```
c("Hi, I am Magic method Call") 
('Hi, I am Magic method Call',)
{}

c.show("Hi, I am instance method")
Hi, I am instance method

```

