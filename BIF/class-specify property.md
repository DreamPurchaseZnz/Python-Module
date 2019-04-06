# Managing class attributes in python
We are trying to get the attribute or set the attribute of an object which is very common in all python programs
especially when working with classes
```
object.attribute or object.attribute = value`
```

Sometimes we want to hook into the attribute and perform some changes to it.
```
>>> obj.attribute
>>> obj.attribute = value
```
Features, here are some python features that help us manage attribute access in our code
```
__getattr__ 
__setattr__
Property Protocol
```
For a class, we can check out what attributes are under this class object

```
object.__dict__                    # return dictionary of the key value pair of object attributes
object.__dict__.keys()
```
To access and set attribute, we can do the following：
```
setattr(object, key, values)
getattr(object, key)
```

## Property protocol
```
class property(fget=None, fset=None, fdel=None, doc=None)
fget                 ---> a function for getting an attribute value
fset                 ---> a function for setting an attribute value
fdel                 ---> a function for deleting an attribute value
doc                  ---> create a docstring for the attribute
```
A typical use is define a **managed** attribute x:
```
class C:
    def __init__(self):
        self._x = None
        
    # ----------------------------------------------------------
    # print more beautiful style , not just a value
    def getx(self):
        return self._x
        
    # ----------------------------------------------------------
    # you can set a limit for a value
    def setx(self, value):
        self._x = function(x)

    def delx(self):
        del self._x

    x = property(getx, setx, delx, "I'm the 'x' property.")

```
if c is an instance of C  
```
c.x                              ---> it will invoke the getter method;
c.x = value                      ---> it will invoke the setter
del c.x                          ---> it will invoke the deleter
doc x                            
```

The  @ property  decorater turns method into a **'getter'** for only a read-only attribute with the same name.

```
class Person(object):
    """"""
    # ----------------------------------------------------------------------
    def __init__(self, first_name, last_name):
        """Constructor"""
        self.first_name = first_name
        self.last_name = last_name
    # ----------------------------------------------------------------------
    @property
    def full_name(self):
        """
        Return the full name
        """
        return "%s %s" % (self.first_name, self.last_name)
```
```
p = Person('mike','judy')
p.full_name
Out[9]: 
'mike judy'
p.first_name
Out[10]: 
'mike'
p.full_name = 'Mike Jackon'
Traceback (most recent call last):
  File "C:\Program Files\Anaconda3\lib\site-packages\IPython\core\interactiveshell.py", line 2881, in run_code
    exec(code_obj, self.user_global_ns, self.user_ns)
  File "<ipython-input-11-d42cabdeb4ef>", line 1, in <module>
    p.full_name = 'Mike Jackon'
AttributeError: can't set attribute

```
A property object has getter,setter and deleter methods usable as decorators

that create a copy of the property with the corresponding accessor function set to decorated function

This is best explained with an example
```
class C:
    def __init__(self):
        self._x = None

    @property
    def x(self):
        """I'm the 'x' property."""
        return self._x

    @x.setter
    def x(self, value):
        self._x = value

    @x.deleter
    def x(self):
        del self._x

```
This code is exactly equivalent to the first example.

Be sure to give the additonal functions  the same name as the original property(x in case)







