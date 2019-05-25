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
## [Namedtuple](https://www.reddit.com/r/Python/comments/38ee9d/intro_to_namedtuple/)
Returns a new tuple subclass named typename.
The new subclass is used to create tuple-like objects 
that have fields accessible by attribute lookup as well as being indexable and iterable
```
collections.namedtuple(
typename,                     # This is the name of the new tuple subclass 
field_names,                  # a sequence of names for each field. 
                                It can be a sequence as in a list ['x', 'y', 'z'] 
                                or string x y z (without commas, just whitespace) or x, y, z.
rename=False, 
defaults=None,                # If verbose is True, the class definition is printed 
                                just before being built
module=None)               
```

```
Personfunc = namedtuple('Person', 'name age gender')
Personfunc                                           # decorator tentatively
<class '__main__.Person'>
```
### namedtuple Vs tuple
Named tuple instances can be referenced using object-like variable dereferencing or the standard tuple syntax. 
They can be used similarly to struct or other common record types, except that they are immutable. 

```
import collections

Person = collections.namedtuple('Person', 'name age gender') # field seperated by space
bob = Person(name='Bob', age=30, gender='male')
bob                                                       # Person(name='Bob', age=30, gender='male')
print ('%s is a %d year old %s' % bob)                    # Fields by index
```
In nature, it is a tupe with named field.
```
pt1 = (1.0, 5.0)
pt2 = (2.5, 1.5)

from math import sqrt
line_length = sqrt((pt1[0]-pt2[0])**2 + (pt1[1]-pt2[1])**2)
```
We can reference the feild when we use the namedtuple
```
from collections import namedtuple
Point = namedtuple('Point', 'x y')          # container
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

## Access Operations
```
index              # Access by keyname is also allowed as in dictionaries
keyname            # This is yet another way to access the value by 
                     giving namedtuple and key value as its argument
getattr
```
```
Student = collections.namedtuple('Student',['name','age','DOB']) 
S = Student('Nandini','19','2541997') 

print ("The Student age using index is : ",end ="") 
print (S[1]) 

print ("The Student name using keyname is : ",end ="") 
print (S.name) 

print ("The Student DOB using getattr() is : ",end ="") 
print (getattr(S,'DOB')) 

```
```
The Student age using index is : 19
The Student name using keyname is : Nandini
The Student DOB using getattr() is : 2541997
```

### Conversion Operations
```
_make()                    # return a namedtuple() from the iterable passed as argument.
_asdict()                  # OrdereDict() as constructed from the mapped values of namedtuple().
**                         # convert a dictionary into the namedtuple().
```
```
Student = collections.namedtuple('Student',['name','age','DOB']) 
S = Student('Nandini','19','2541997') 

li = ['Manjeet', '19', '411997' ] 
di = { 'name' : "Nikhil", 'age' : 19 , 'DOB' : '1391997' } 

Student._make(li)
S._asdict() 
Student(**di)
```
```
Student(name='Manjeet', age='19', DOB='411997')
OrderedDict([('name', 'Nandini'), ('age', '19'), ('DOB', '2541997')])
Student(name='Nikhil', age=19, DOB='1391997')
```
### Additional Operations
```
_fields               # return all the keynames of the namespace declared.
_replace()            # change the values mapped with the passed keyname.
```
```
Student = collections.namedtuple('Student',['name','age','DOB']) 
S = Student('Nandini','19','2541997') 

print (S._fields) 
print(S._replace(name = 'Manjeet')) 

```




