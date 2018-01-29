# [Operators](https://docs.python.org/3.4/library/operator.html)
Standard operators as functions

The operator module exports a set of efficient functions corresponding to the intrinsic operators of Python. For example, operator.add(x, y) is equivalent to the expression x+y. The function names are those used for special class methods; variants without leading and trailing __ are also provided for convenience.

The functions fall into categories that perform
- object comparisons
- logical operations
- mathematical operations 
- sequence operations.



## [What are operators in python?](https://www.programiz.com/python-programming/operators)
Operators are special symbols in python that carry out arithmetic or logical computation, the value that the operator operates on is called
operand.
```
2+3  # 5
```

## Arithmetic operators
Arithmetic operators are used to perform mathematical operations like addition, substraction, multiplication.
``` 
Operator       Meaning                                                         Example
+              Add two operands or unary plus                                  x + y
-              Subtract right operand from the left or unary minus             x - y
*              Multiply two operands                                           x * y
/              Divide left operand by the right one 
               (always results into float)                                     x / y
%              Modulus - remainder of the division of 
               left operand by the right                                       x % y (remainder of x/y)
//             Floor division - 
               division that results into whole number 
               adjusted to the left in the number line                         x // y
**             Exponent - left operand raised to the power 
               of right                                                        x**y (x to the power y)
```
```
15//4  # 3
```

## Comparison operators
Comparision operators are used to compare values, it easier return True or False according to the condition.
```
Operator  Meaning                                                         Example
>         Greater that - True if left operand is greater than the right   x > y
<         Less that - True if left operand is less than the right         x < y
==         Equal to - True if both operands are equal                     x == y
!=         Not equal to - True if operands are not equal                  x != y
>=         Greater than or equal to - True if left operand 
           is greater than or equal to the right                          x >= y
<=         Less than or equal to - True if left operand is 
           less than or equal to the right                                x <= y
```
```
12 != 10   # True

```


## Logical operators
Logical operators are the *and*, *or*, *not* operators
```
Operator              Meaning                                Example
and                  True if both the operands are true	     x and y
or                   True if either of the operands is true  x or y
not                  True if operand is false 
                     (complements the operand)               not x
```

## Bitwise operators
Bitwise operators act on operands as if they are string of binary digits. it operates bit by bit, hence the name
For example, 2 is 10 in binary and 7 is 111
In the table below: Let x = 10 (0000 1010 in binary) and y = 4 (0000 0100 in binary)
```
Operator                    Meaning                      Example
&                           Bitwise AND                  x& y = 0 (0000 0000)
|                           Bitwise OR                   x | y = 14 (0000 1110)
~                           Bitwise NOT                  ~x = -11 (1111 0101)
^                           Bitwise XOR                  x ^ y = 14 (0000 1110)
>>                          Bitwise right shift          x>> 2 = 2 (0000 0010)
<<                          Bitwise left shift           x<< 2 = 40 (0010 1000)
```
It is to horrible when you naturally take the operator *^* as the exponent operator. It's totally wrong. for example you want this
10^4 = 10000,but got 14 in python, and you don't know, that will cost a lot of time to capture the error.
```
10^4  # 14
10&4  # 0
10|4  # 14
10>>2 # 2
10<<2 # 40
```
## Assignment operators
assignment operators are used in Python to assign values to variables
There are various compound operators in Python like a += 5 that adds to the variable 
and later assigns the same. It is equivalent to a = a + 5.
```
Operator                 Example                      Equivatent to
=                        x = 5                        x = 5
+=                       x += 5                       x = x + 5
-=                       x -= 5                       x = x - 5
*=                       x *= 5                       x = x * 5
/=                       x /= 5                       x = x / 5
%=                       x %= 5                       x = x % 5
//=                      x //= 5                      x = x // 5
**=                      x **= 5                      x = x ** 5
&=                       x &= 5                       x = x & 5
|=                       x |= 5                       x = x | 5
^=                       x ^= 5                       x = x ^ 5
>>=                      x >>= 5                      x = x >> 5
<<=                      x <<= 5                      x = x << 5
```


## Special operators
python language offers some special type of operators like the identity operator or the membership operator, they are 
discribed below with examples.
### identity operators
*is*  and *is not* are the indentity operators in python, they are used to check if two values(or variables) are located on the same
part of the memory. Two variables that are equal does not imply that they are identitical
```
Operator  Meaning                                                                  Example
is        True if the operands are identical (refer to the same object)            x is True
is not    True if the operands are not identical (do not refer to the same object) x is not True
```
```
x1 = 5
y1 = 5
x2 = 'Hello'
y2 = 'Hello'
x3 = [1,2,3]
y3 = [1,2,3]

x1 is not y1 # False  --> integers of same values,
x2 is y2     # True   --> strings
x3 is y3     # False  --> They are equal but not identical. Since list are mutable
```

### Membership operators
*in* and *not in* are the membership operators in Python, they are used to test wether a variable or value is found in a sequence.
(string, list, tuple, set and dictionary).

In the dictionary we can only test for presence of key, not the value.
```
Operator                  Meaning                                             Example
in                        True if value/variable is found in the sequence     5 in x
not in                    True if value/variable is not found in the sequence 5 not in x
```
```
x = 'Hello world'
y = {1:'a',2:'b'}
1 in y     # True
x not in y # True
```
## Operations which work with sequences 
```
Operator                                         Meaning
operator.concat(a, b) 
operator.contains(a, b)                          Test b in a              
operator.countOf(a, b)                           Return the occurrences of b in a
operator.delitem(a, b)                           Del the value of a in b
operator.getitem(a, b)                           Get the value of a in b
operator.indexOf(a, b)                  
operator.setitem(a, b, c)                        Set the value of a at index b to c

```
## [Operator defines tools for generalized attribute and item lookups](https://docs.python.org/3.4/library/operator.html)

Take the function as the operand.

```
operator.attrgetter(attr)                                 
operator.attrgetter(*attrs)
```
Return a callable object that fetches *attr* from its operand, the attribute names can alse contain dots.

- After f = attrgetter('name'), the call f(b) returns b.name.
- After f = attrgetter('name', 'date'), the call f(b) returns (b.name, b.date).
- After f = attrgetter('name.first', 'name.last'), the call f(b) returns (b.name.first, b.name.last).

```
operator.itemgetter(item)
operator.itemgetter(*items)
```
Return a callable object that fetches item from its operand using the operand's \__getitem\__() method.


- After f = itemgetter(2), the call f(r) returns r\[2].
- After g = itemgetter(2, 5, 3), the call g(r) returns (r\[2], r\[5], r\[3]).

```
def itemgetter(*items):
    if len(items) == 1:
        item = items[0]
        def g(obj):
            return obj[item]
    else:
        def g(obj):
            return tuple(obj[item] for item in items)
    return g
```
Example of using itemgetter() to retrieve specific field from a tuple record
```
inventory = [('apple', 3), ('banana', 2), ('pear', 5), ('orange', 1)]
from operator import itemgetter
getcount = itemgetter(1)
list(map(getcount, inventory))
Out[8]: 
[3, 2, 5, 1]
sorted(inventory, key=getcount)
Out[9]: 
[('orange', 1), ('banana', 2), ('apple', 3), ('pear', 5)]
```

```
operator.methodcaller(name[, args...])
```
Return a callable object that calls the method name on its operand.

- After f = methodcaller('name'), the call f(b) returns b.name().
- After f = methodcaller('name', 'foo', bar=1), the call f(b) returns b.name('foo', bar=1).




