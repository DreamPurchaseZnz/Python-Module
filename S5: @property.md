# property
class property(fget=None, fset=None, fdel=None, doc=None)
```
fget                 ---> a function for getting an attribute value
fset                 ---> a function for setting an attribute value
fdel                 ---> a function for deleting an attribute value
doc                  ---> create a docstring for the attribute
```
A typical use is define a managed atr
```
class C:
    def __init__(self):
        self._x = None

    def getx(self):
        return self._x

    def setx(self, value):
        self._x = value

    def delx(self):
        del self._x

    x = property(getx, setx, delx, "I'm the 'x' property.")

```

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

```
from decimal import Decimal
########################################################################
class Fees(object):
    """"""
    # ----------------------------------------------------------------------
    def __init__(self):
        """Constructor"""
        self._fee = None
    # ----------------------------------------------------------------------
    @property
    def fee(self):
        """
        The fee property - the getter
        """
        return self._fee
    # ----------------------------------------------------------------------
    @fee.setter
    def fee(self, value):
        """
        The setter of the fee property
        """
        if isinstance(value, str):
            self._fee = Decimal(value)
        elif isinstance(value, Decimal):
            self._fee = value
            
f = Fees()
f.fee= '1'
f.fee
Out[29]: 
Decimal('1')



```
