# Class
Way of packaging Variables and Functions together: Attribute and Action

### Usage

the class inheritance mechanism allows **multiple base classes**, <br>
a derived class can **override** any methods of its **base class or classes**, <br>
and **a method can call the method** of a base class with the same name. <br>

## Python Scopes and Namespaces
A namespace is a mapping from names to objects.<br>
Most namespaces are currently implemented as Python dictionaries

### Namescope

Examples of namespaces are:
```
Different NameSpaces                                           Different lifetime
the set of built-in names                          ---> When Python interpreter starts up,Never delete
the global names in a module                       ---> when the module definition is read in,Until the python quits
the local names in a function invocation           ---> when the function is called
                                                        Deleted when the function returns or raises an exception
```
The important thing to know about namespaces is that there is absolutely no relation between names in different namespaces

### Lifetime

Namespaces are created at different moments and have different lifetimes,<br>
**The statements** executed by the top-level invocation of the interpreter, <br>
either read from a script file or interactively, are considered part of a module called __main__,<br>
so they have their own global namespace

### Accessible

A scope is a textual region of a Python program where a namespace is directly accessible:<br>
At any time during execution, there are at least three nested scopes whose namespaces are directly accessible:
```
the innermost scope                         ---> which is searched first, contains the local names
the scopes of any enclosing functions       ---> which are searched starting with the nearest enclosing scope,
                                                 contains non-local, but also non-global names
the next-to-last scope                      ---> the current module’s global names
the outermost scope                         ---> (searched last) is the namespace containing built-in names
```
All variables found outside of the innermost scope are read-only except a name is declared global<br>
An attempt to write to such a variable will samplely create a **New local variable** in the intermost scope,<br>
leaving the identically named outer variable unchanged

### Assignments

It is important to realize that scopes are determined textually<br>
Assignments do not copy data — they just **bind names** to objects.<br>
The same is true for deletions: the statement del x **removes the binding** of x from the namespace referenced by the local scope

### Attribute

Attribute for any name following a dot.references to names in modules are attribute references:
```
in the expression modname.funcname, modname is a module object and funcname is an attribute of it
```
Attributes may be read-only or writable

## A First Look at Classes

### Class Definition Syntax

```
class ClassName:
    <statement-1>
    .
    .
    .
    <statement-N>
```
When a class definition is entered, a new namespace is created, and used as the local scope 

### Class Objects

Class objects support two kinds of operations:**attribute references** and **instantiation**

1. Attribute references use the standard syntax used for all attribute references in Python:
```
obj.name             ---> Standard syntax
```
Valid attribute names are **all the names** that were in the class’s namespace when the class object was created,<br>
Class attributes can also be assigned to
```
. __doc__ is also a valid attribute            ---> docstring belonging to the class

```
2. Class instantiation can be seen as parameterless function that returns a new instance of the class

create objects with instances customized to a specific initial state
```
__init__()          ---> initialized instance; have arguments for greater flexibility

```
for a subclass, if the \__init\__ is not difined , this method will be pass to the subclass as the initial state.
if  \__init\__ is find in the subclass, the baseclass method will be abandoned, there is a method can resolve the 
problem: super() method
```
class A:
    def __init__(self,a=1):
        self.a = a
        
class B(A):
    print('b')

c = B(2)
>>c.a
>>2
```
```
class C(A):
    def __init__(self, c=1):
        self.c = c
        
d = C()
>>d.c 
>>1
>>d.a
>>AttributeError: 'C' object has no attribute 'a'
```
To achieve this
```
class A:
  def __init__(self):
   print "enter A"
   print "leave A"

 class B(A):
  def __init__(self):
   print "enter B"
   A.__init__(self)
   print "leave B"

 >>> b = B()
 enter B
 enter A
 leave A
 leave B
```
One method
```
class B(C):    # A --> C
  def __init__(self):
   print "enter B"
   C.__init__(self) # A --> C
   print "leave B"
```
other method-super

```
class A(object):    # A must be new-style class
  def __init__(self):
   print "enter A"
   print "leave A"

class B(C):     # A --> C
  def __init__(self):
   print "enter B"
   super(B, self).__init__()
   print "leave B"
```

### Instance Objects

The only operations understood by instance objects are attribute references: **data attributes** and **methods**.
```
data attributes correspond to “instance variables”
A method is a function that “belongs to” an object
```

### Method Objects- class method and instance method

the special thing about methods is that the object is passed as the first argument of the function,<br>
the first argument of a instance method is called *self*. This is nothing more than a convention. And
class method called *cls*. 

> The class method can be called on both an instance and the class itself. 

> The instance method is only called on the instance of a class. we should emphasize that the instance of a class.
```
class method:
    @classmethod
    def tell(cls, message):
        print(cls.__name__,':',message)
    def show(self, information):
        print('This is instance method:' + information)
        
method.tell('class method')
method : class method
method.show('class method')
Traceback (most recent call last):
  File "C:\Program Files\Anaconda3\lib\site-packages\IPython\core\interactiveshell.py", line 2881, in run_code
    exec(code_obj, self.user_global_ns, self.user_ns)
  File "<ipython-input-37-b94f5af70d6b>", line 1, in <module>
    method.show('class method')
TypeError: show() missing 1 required positional argument: 'information'

mt = method()
mt.show('instance method')
This is instance method:instance method
mt.tell('class method')
method : class method



```


### Class and Instance Variables

Generally speaking,
```
instance variables        are for data unique to each instance 
class variables           are for attributes and methods shared by all instances of the class
```
Variables inside and outside of a class \__init\__() function

1. class variables:  Elements outside the \__init\__ method are static elements, it means, they belong to the class.

2. instance variables: Elements inside the \__init\__ method are elements of the object (self), they don't belong to the class.

e.g
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
Same results

Nothing new so far ...
Let's try changing the static element or class variable
```
MyClass.static_elem = 999
```
we can see all the instance all change to 999, it means the class variable shared by all the instance.
```
>>> print c1.static_elem, c1.object_elem
999 456
>>> print c2.static_elem, c2.object_elem
999 456
```

Now, let's try changing the object element- instance variable
```
c1.object_elem = 888
```
the instance variable don't change, it mean instance variable are unique. 
```
>>> print c1.static_elem, c1.object_elem
999 888
>>> print c2.static_elem, c2.object_elem
999 456
```
second example:

class shared data can have possibly surprising effects with involving mutable objects such as lists and dictionaries
```
class Dog:

    tricks = []             # mistaken use of a class variable

    def __init__(self, name):
        self.name = name

    def add_trick(self, trick):
        self.tricks.append(trick)

>>> d = Dog('Fido')
>>> e = Dog('Buddy')
>>> d.add_trick('roll over')
>>> e.add_trick('play dead')
>>> d.tricks                # unexpectedly shared by all dogs
['roll over', 'play dead']

```

Correct design of the class should use an instance variable instead:

```
class Dog:

    def __init__(self, name):
        self.name = name
        self.tricks = []    # creates a new empty list for each dog

    def add_trick(self, trick):
        self.tricks.append(trick)

>>> d = Dog('Fido')
>>> e = Dog('Buddy')
>>> d.add_trick('roll over')
>>> e.add_trick('play dead')
>>> d.tricks
['roll over']
>>> e.tricks
['play dead']

```

## Random Remarks

### The same name
Data attributes override method attributes with the same name

### Function definition
2. Any function object that is a class attribute defines a method for instances of that class. <br>
It is not necessary that the function definition is textually enclosed in the class definition:<br>
assigning a function object to a local variable in the class is also ok. For example:

```
# Function defined outside the class
def f1(self, x, y):
    return min(x, x+y)

class C:
    f = f1

    def g(self):
        return 'hello world'

    h = g
```
 h being exactly equivalent to g. Note that this practice usually only serves to confuse the reader of a program.
 
### Cross reference

Methods may call other methods by using method attributes of **the self argument**:
 
 ```
 class Bag:
    def __init__(self):
        self.data = []

    def add(self, x):
        self.data.append(x)

    def addtwice(self, x):
        self.add(x)
        self.add(x)
 
 ```
Methods may reference global names in the same way as ordinary functions, The global scope associated with a method is the module containing its definition.

Access static class variables within class methods
```
class Foo(object):
    bar = 1
    def bah(self):
        print(slef.bar)
        print(Foo.bar)
```

### Import modules
there are many legitimate uses of the global scope:
functions and modules imported into the global scope can be used by methods, as well as functions and classes defined in it


## Inheritance

### The syntax for a derived class definition 

looks like this
```
class DerivedClassName(BaseClassName):
    <statement-1>
    .
    .
    .
    <statement-N>
```
the base class is defined in another module
```
class DerivedClassName(modname.BaseClassName):
```
### Execution

Execution of a derived class definition proceeds the same as for a base class. <br>
When the class object is constructed, the base class is remembered.This is used for resolving **attribute references**:<br>
if a requested attribute is not found in the class, the search proceeds to look in the base class.<br>
This rule is applied **recursively** if the base class itself is derived from some other class

for **variable**(class variable and instance variable), the situation is different

1. class variable can be inherited directly
2. instance varialbe need to use **super menthod**

**Method references** are resolved as follows:<br>
the corresponding class attribute is searched, <br>
descending down the chain of base classes if necessary,<br>
and the method reference is valid if this yields a function object

Derived classes may override methods of their base classes.
An overriding method in a derived class may in fact want to extend rather than simply replace the base class method of the same name. 
There is a simple way to call the base class method directly: 
```
just call BaseClassName.methodname(self, arguments). This is occasionally useful to clients as well
```

### BIF

Python has two built-in functions that work with inheritance

```
isinstance()            to check an instance’s type
Use issubclass()        to check class inheritance:
```

### Multiple Inheritance

Python supports a limited form of multiple inheritance as well
```
class DerivedClassName(Base1, Base2, Base3):
    <statement-1>
    .
    .
    .
    <statement-N>

```

For old-style classes, the only rule is depth-first, left-to-right<br>

With new-style classes, dynamic ordering is necessary because all cases of multiple inheritance exhibit one or more diamond relationships (where at least one of the parent classes can be accessed through multiple paths from the bottommost class)

## Private Variables and Class-local References

Private” instance variables that cannot be accessed except from inside an object don’t exist in Python.It should be considered an implementation detail and subject to change without notice

Any identifier of the form __spam (at least two leading underscores, at most one trailing underscore) is textually replaced with _classname__spam, where classname is the current class name with leading underscore(s) stripped

Remain Question！！

Like Structure
```
class Employee:
    pass

john = Employee()  # Create an empty employee record

# Fill the fields of the record
john.name = 'John Doe'
john.dept = 'computer lab'
john.salary = 1000

```

# How to override a class method in python
## class method Vs instance method
I guess the class method may provide some neccessary information for the user.
a class method in python differs from an instance method in a couple importance ways:
```
1. It binds to a class rather than an instance. Thus, its first argument is a class, 
   often called cls rather than the usual self.

2. It can be called on both an instance of a class and the class itself.
```
```
class Spam(object):
    @classmethod
    def parrot(cls, message):
        print(cls.__name__, "says:", message)

class Eggs(Spam):
    @classmethod
    def parrot(cls, message):
        super(Eggs, cls).parrot(message)
        
Eggs.parrot("Hello, world!")
Eggs says: Hello, world!

s = Spam()                                        ---> instance the class, the class method also work
s.parrot('Hello')
Spam says: Hello

```
```
class Eggs(Spam):
    pass
Eggs.parrot("Hello, world!")
Eggs says: Hello, world!
```






