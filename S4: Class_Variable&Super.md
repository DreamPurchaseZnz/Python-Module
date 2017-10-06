Variables inside and outside of a class __init__() function
--------------------------------------------------------------------------------

1. Elements outside the __init__ method are static elements, it means, they belong to the class.

2. Elements inside the __init__ method are elements of the object (self), they don't belong to the class.

```
class MyClass:
    static_elem = 123

    def __init__(self):
        self.object_elem = 456

c1 = MyClass()
c2 = MyClass()
```

Initial values of both elements
```
>>> print c1.static_elem, c1.object_elem 
123 456
>>> print c2.static_elem, c2.object_elem
123 456
```

Nothing new so far ...
Let's try changing the static element
```
MyClass.static_elem = 999
```
```
>>> print c1.static_elem, c1.object_elem
999 456
>>> print c2.static_elem, c2.object_elem
999 456
```

Now, let's try changing the object element
```
c1.object_elem = 888
```
```
>>> print c1.static_elem, c1.object_elem
999 888
>>> print c2.static_elem, c2.object_elem
999 456
```

## super
```
class ClassA(object):
    def __init__(self):
        self.var1 = 1
        self.var2 = 2
    def method(self):
        self.var1 = self.var1 + self.var2
        return self.var1

class ClassB(ClassA):
    def __init__(self):
    
```
[super](https://docs.python.org/2/library/functions.html#super) let you avoid referring to the base class explicitly, which can be nice. [post](https://rhettinger.wordpress.com/2011/05/26/super-considered-super/)
```
class Base(object):
    def __init__(self):
        print ("Base created")
        self.var = 10

class ChildA(Base):
    def __init__(self):
        Base.__init__(self)
        print('this is the child A')
        self.var = 12

class ChildB(Base):
    def __init__(self):
        super().__init__()
        print('this is the child B')
        self.var = 14

```
the child modify the value of var
```
a = ChildA()
Out[22]:
Base created
this is the child A

a.var
Out[23]: 
12
```
```
b = ChildB()
Base created
this is the child B
b.var
Out[26]: 
14
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
    print ("first")

class Second(object):
  def __init__(self):
    super(Second, self).__init__()
    print ("second")

class Third(First, Second):
  def __init__(self):
    super(Third, self).__init__()
    print ("that's it")

```
the result:
```
>>> x = Third()
second
first
that's it
```

the order to resolve \__init\__ is calculated (before Python 2.3) using a "depth-first left-to-right traversal" :

a simple depth-first left-to-right scheme(http://python-history.blogspot.com/2010/06/method-resolution-order.html)
```
class A:
  def save(self): pass

class B(A): pass

class C(A):
  def save(self): pass

class D(B, C): pass

```
Here, class D inherits from B and C, both of which inherit from class A.

Using the classic MRO, methods would be found by searching the classes in the order D, B, A, C, A

However, this is unlikely what you want in this case! Since both B and C inherit from A, one can argue that the redefined method C.save() is actually the method that you want to call,**since it can be viewed as being "more specialized" than the method in A**

