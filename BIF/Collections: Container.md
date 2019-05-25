# Container
--------------------------------------------------------------------------
[This module implements specialized container datatypes providing alternatives to Python’s general purpose built-in containers, dict, list, set, and tuple.](https://docs.python.org/3.5/library/collections.html?highlight=defaultdict#collections.defaultdict)
```
namedtuple                        
deque          
ChainMap          
Counter          
OrderedDict          
defaultdict                                             
UserDict         
UserList          
UserString          
```
```
namedtuple()                # factory function for creating tuple subclasses with named fields
deque                       # list-like container with fast appends and pops on either end
ChainMap                    # dict-like class for creating a single view of multiple mappings
Counter                     # dict subclass for counting hashable objects
OrderedDict                 # dict subclass that remembers the order entries were added
defaultdict                 # dict subclass that calls a factory function to supply missing values
UserDict                    # wrapper around dictionary objects for easier dict subclassing
UserList                    # wrapper around list objects for easier list subclassing
UserString                  # wrapper around string objects for easier string subclassing
```



### defaultdict
return a new dictionary-like object. 
It ignores a method and add a writable instance variable. the function is same as **dict**(key-value pair):
```
__missing__(key)
default_factory                                       ---> Key type argument(list,set,int...)         
``` 

Dict Operation Supported
```
len
d[key]
get(key)
d[key] = value
setdefault                                           ---> If not, insert key with a value of default 

# Delete operation                                                        
del d[key]
pop                                                 
popitem
clear
copy

# Acquire information
key in d                                            ---> True if key exists
key not in d
iter                                                ---> For in iterations

# Get value
fromkeys
update                                              ---> Update the dictionary with the key/value pairs from other
items                                               ---> View objects 
values                                              ---> Dynamic view on dictionary'entries
keys                                                ---> Iteration
```
e.g.
```
from collections import defaultdict
s = [('yellow', 1), ('blue', 2), ('yellow', 3), ('blue', 4), ('red', 1)] # iterable
d = defaultdict(list) # Given a type
for k, v in s:
  d[k].append(v)      # List Append method to dict value
  
sorted(d.items())
```
## [namedtuple](https://www.reddit.com/r/Python/comments/38ee9d/intro_to_namedtuple/)
Returns a new tuple subclass named typename.
The new subclass is used to create tuple-like objects 
that have fields accessible by attribute lookup as well as being indexable and iterable
```
collections.namedtuple(
typename, 
field_names, 
*, 
rename=False, 
defaults=None, 
module=None)               
```
Named tuples are basically easy-to-create, lightweight object types. Named tuple instances can be referenced using object-like variable dereferencing or the standard tuple syntax. They can be used similarly to struct or other common record types, except that they are immutable. 

```
import collections

Person = collections.namedtuple('Person', 'name age gender')
bob = Person(name='Bob', age=30, gender='male')
jane = Person(name='Jane', age=29, gender='female')

for p in [ bob, jane ]:
    print '%s is a %d year old %s' % p
```
```
Fields by index:
Bob is a 30 year old male
Jane is a 29 year old female
```
```
pt1 = (1.0, 5.0)
pt2 = (2.5, 1.5)

from math import sqrt
line_length = sqrt((pt1[0]-pt2[0])**2 + (pt1[1]-pt2[1])**2)
```
```
from collections import namedtuple
Point = namedtuple('Point', 'x y')
pt1 = Point(1.0, 5.0)
pt2 = Point(2.5, 1.5)

from math import sqrt
line_length = sqrt((pt1.x-pt2.x)**2 + (pt1.y-pt2.y)**2)
```
Furthermore, you can also replace ordinary immutable classes that have no functions, only fields with them. You can even use your named tuple types as base classes:
```
class Point(namedtuple('Point', 'x y')):   # explictly
    pass
pt = Point("1", "2")

Point = namedtuple('Point', 'x y')         # implictly
pt = Point("1", "2")

 namedtuple('Point', 'x y')                # nothing
```
```
class whatsmypurpose(tuple):
    'whatsmypurpose(x, y)'
    __slots__ = ()
    _fields = ('x', 'y')
    def __new__(_cls, x, y):
        'Create new instance of whatsmypurpose(x, y)'
        return _tuple.__new__(_cls, (x, y))
    @classmethod
    def _make(cls, iterable, new=tuple.__new__, len=len):
        'Make a new whatsmypurpose object from a sequence or iterable'
        result = new(cls, iterable)
        if len(result) != 2:
            raise TypeError('Expected 2 arguments, got %d' % len(result))
        return result
    def _replace(_self, **kwds):
        'Return a new whatsmypurpose object replacing specified fields with new values'
        result = _self._make(map(kwds.pop, ('x', 'y'), _self))
        if kwds:
            raise ValueError('Got unexpected field names: %r' % list(kwds))
        return result
    def __repr__(self):
        'Return a nicely formatted representation string'
        return self.__class__.__name__ + '(x=%r, y=%r)' % self
    def _asdict(self):
        'Return a new OrderedDict which maps field names to their values.'
        return OrderedDict(zip(self._fields, self))
    def __getnewargs__(self):
        'Return self as a plain tuple.  Used by copy and pickle.'
        return tuple(self)
    x = _property(_itemgetter(0), doc='Alias for field number 0')
    y = _property(_itemgetter(1), doc='Alias for field number 1')
```
### Access Operations


1. Access by index : The attribute values of namedtuple() are ordered and can be accessed using the index number unlike dictionaries which are not accessible by index.

2. Access by keyname : Access by keyname is also allowed as in dictionaries.

3. using getattr() :- This is yet another way to access the value by giving namedtuple and key value as its argument.
```
# Python code to demonstrate namedtuple() and 
# Access by name, index and getattr() 

# importing "collections" for namedtuple() 
import collections 

# Declaring namedtuple() 
Student = collections.namedtuple('Student',['name','age','DOB']) 

# Adding values 
S = Student('Nandini','19','2541997') 

# Access using index 
print ("The Student age using index is : ",end ="") 
print (S[1]) 

# Access using name 
print ("The Student name using keyname is : ",end ="") 
print (S.name) 

# Access using getattr() 
print ("The Student DOB using getattr() is : ",end ="") 
print (getattr(S,'DOB')) 

```
```
The Student age using index is : 19
The Student name using keyname is : Nandini
The Student DOB using getattr() is : 2541997
```

### Conversion Operations
1. \_make() :- This function is used to return a namedtuple() from the iterable passed as argument.

2. \_asdict() :- This function returns the OrdereDict() as constructed from the mapped values of namedtuple().

3. using “\*\*” (double star) operator :- This function is used to convert a dictionary into the namedtuple().

```
# Python code to demonstrate namedtuple() and 
# _make(), _asdict() and "**" operator 

# importing "collections" for namedtuple() 
import collections 

# Declaring namedtuple() 
Student = collections.namedtuple('Student',['name','age','DOB']) 

# Adding values 
S = Student('Nandini','19','2541997') 

# initializing iterable 
li = ['Manjeet', '19', '411997' ] 

# initializing dict 
di = { 'name' : "Nikhil", 'age' : 19 , 'DOB' : '1391997' } 

# using _make() to return namedtuple() 
print ("The namedtuple instance using iterable is : ") 
print (Student._make(li)) 

# using _asdict() to return an OrderedDict() 
print ("The OrderedDict instance using namedtuple is : ") 
print (S._asdict()) 

# using ** operator to return namedtuple from dictionary 
print ("The namedtuple instance from dict is : ") 
print (Student(**di)) 
```
```
The namedtuple instance using iterable is  : 
Student(name='Manjeet', age='19', DOB='411997')
The OrderedDict instance using namedtuple is  : 
OrderedDict([('name', 'Nandini'), ('age', '19'), ('DOB', '2541997')])
The namedtuple instance from dict is  : 
Student(name='Nikhil', age=19, DOB='1391997')
```
### Additional Operations
1. \_fields :- This function is used to return all the keynames of the namespace declared.

2. \_replace() :- This function is used to change the values mapped with the passed keyname.

```
# Python code to demonstrate namedtuple() and 
# _fields and _replace() 

# importing "collections" for namedtuple() 
import collections 

# Declaring namedtuple() 
Student = collections.namedtuple('Student',['name','age','DOB']) 

# Adding values 
S = Student('Nandini','19','2541997') 

# using _fields to display all the keynames of namedtuple() 
print ("All the fields of students are : ") 
print (S._fields) 

# using _replace() to change the attribute values of namedtuple 
print ("The modified namedtuple is : ") 
print(S._replace(name = 'Manjeet')) 

```




