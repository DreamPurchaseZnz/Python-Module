# Python
## Python syntax- if & for
That's more specifically a ternary operator expression than an if-then, here's the python syntax
```
value_when_true if condition else value_when_false
[value_false, value_true][<test>]
[lambda: value_false, lambda: value_true][<test>]()
[Loop value for i in range(size)]
```
e.g.
```
count = 0 if count == N else N + 1
count = [0,N+1][count==N]
count = [lambda:0, lambda:N+1][count==N]()
```
e.g.
```
f = [e for e in range(10) for _ in range(10)]),[sample_size,1]
```
## unpacks an dictionary into keyword arguments

```
list or tupe  --- * unpack ---> call function --- positional argument  --- function --- * collects ---> a tupe
a dictionary --- ** unpack  ---> call function --- keyword argument --- function --- ** collects ---> a dictionary 
```
### Inside a function header
```
*    ---> collects all the positional arguments in a tuple
**   ---> collects all the keyword arguments in a dictionary
```
```
>>> def functionA(*a, **kw):
       print(a)
       print(kw)


>>> functionA(1, 2, 3, 4, 5, 6, a=2, b=3, c=5)
(1, 2, 3, 4, 5, 6)
{'a': 2, 'c': 5, 'b': 3}
```

### In a function call:
```
* unpacks a list or tuple into position arguments
** unpacks a dictionary into keyword arguments
```
```
>>> lis=[1, 2, 3, 4]
>>> dic={'a': 10, 'b':20}
>>> functionA(*lis, **dic)  #it is similar to functionA(1, 2, 3, 4, a=10, b=20)
(1, 2, 3, 4)
{'a': 10, 'b': 20}
```
## Pack attributes to a dictionary
The syntax of vars() is:
```
vars(object)                                 ---> object can be module, class, instance or any object having __dict__ attribute
```
Return the \__dict__ attribute of the given object
```
class Foo:
    def __init__(self, a=5, b=10):
        self.a = a
        self.b = b
InstanceOfFoo = Foo()
print(vars(InstanceOfFoo))
{'b': 10, 'a': 5}
```
```
Foo.__dict__
Out[36]: 
mappingproxy({'__dict__': <attribute '__dict__' of 'Foo' objects>,
              '__doc__': None,
              '__init__': <function __main__.Foo.__init__>,
              '__module__': '__main__',
              '__weakref__': <attribute '__weakref__' of 'Foo' objects>})
InstanceOfFoo.__dict__
Out[37]: 
{'a': 5, 'b': 10}
```

## Operator - cumulative by stride 
```
-=                                                 ---> subtracts a value from variable, setting the variable to the result
*=                                                 ---> multiplies the variable and a value, making the outcome the variable
/=                                                 ---> divides the variable by the value, making the outcome the variable
%=                                                 ---> performs modulus on the variable, with the variable then being set to the result
```
