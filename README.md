# Python
## super
[super](https://docs.python.org/2/library/functions.html#super) let you avoid referring to the base class explicitly, which can be nice. [post](https://rhettinger.wordpress.com/2011/05/26/super-considered-super/)
```
class Base(object):
    def __init__(self):
        print "Base created"

class ChildA(Base):
    def __init__(self):
        Base.__init__(self)

class ChildB(Base):
    def __init__(self):
        super().__init__()

ChildA() 
ChildB()

```
Note that the syntax changed in Python 3.0: you can just say super().\__init\__() instead of super(ChildB, self).\__init\__() 

It's been noted that in Python 3.0+ you can use
```
super().__init__()
```
to make your call, which is concise and does not require you to reference the parent OR class names explicitly, which can be handy

super work with [mutiple inheritance](https://stackoverflow.com/questions/3277367/how-does-pythons-super-work-with-multiple-inheritance)
```
class First(object):
  def __init__(self):
    super(First, self).__init__()
    print "first"

class Second(object):
  def __init__(self):
    super(Second, self).__init__()
    print "second"

class Third(First, Second):
  def __init__(self):
    super(Third, self).__init__()
    print "that's it"

```

the order to resolve \__init\__ is calculated (before Python 2.3) using a "depth-first left-to-right traversal" :
```
1. According to MRO __init__ of Third is called first.
2. Next, according to the MRO, inside the __init__ method super(Third,self).__init__() 
resolves to the __init__ method of First, which gets called.
3. Inside __init__ of First super(First, self).__init__() calls the __init__ of Second, because that is what the MRO dictates!
4. Inside __init__ of Second super(Second, self).__init__() calls the __init__ of object,
which amounts to nothing. After that "second" is printed.
5. After super(First, self).__init__() completed, "first" is printed.
6. After super(Third, self).__init__() completed, "that's it" is printed.
```
the result:
```
>>> x = Third()
second
first
that's it
```
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
## asterisk *
* Inside a function header
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

* In a function call:
```
* unpacks an list or tuple into position arguments
** unpacks an dictionary into keyword arguments
```
```
>>> lis=[1, 2, 3, 4]
>>> dic={'a': 10, 'b':20}
>>> functionA(*lis, **dic)  #it is similar to functionA(1, 2, 3, 4, a=10, b=20)
(1, 2, 3, 4)
{'a': 10, 'b': 20}
```
