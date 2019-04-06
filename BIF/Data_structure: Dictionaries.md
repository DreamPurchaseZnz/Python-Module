# Dictionaries in python

## Dictionary creation

### Dictionary literals
call dictionary without arguments
```
new_dict = dict()
```
or simply write
```
new_dict ={}
```

for example:
```
# Empty dict
d = {}
# Fill in the entries one by one
d["age"] = 25
```
### From a list of tuples
You can construct a dictionary from a list of key, value pairs
```
d = dict([("age", 25)])
```
```
class Person(object):
    def __init__(self, name, profession):
        self.name = name
        self.profession = profession
 
people = [Person("Nick", "Programmer"), Person("Alice","Engineer")]
professions = dict([ (p.name, p.profession) for p in people ])
>>> print professions
{"Nick": "Programmer", "Alice": "Engineer"}
```

### From two parallel lists
You may have two lists of element, perhas from a database table
```
# Static lists for purpose of illustration
names = ["Nick", "Alice", "Kitty"]
professions = ["Programmer", "Engineer", "Art Therapist"]
```
You may wished to create a dictionary from name to profession. you could do the following:
```
professions_dict = {}
for i in range(len(names)):
    professions_dict[names[i]] = professions[i]
```
This is not ideal, however it involves an explict iterator.
```
# zipped list:
professions_dict = dict(zip(names, professions))
```



## Basic Operation
### Store the variables
```
released = {
		"iphone" : 2007,
		"iphone 3G" : 2008,
		"iphone 3GS" : 2009,
		"iphone 4" : 2010,
		"iphone 4S" : 2011,
		"iphone 5" : 2012
	}
```

### Add the variables
```

released["iphone 5S"] = 2013
```
### Remove a key and it's value
```
del released["iphone"]
```

## Check the length
use the "len()"

### Get variables

use the key to search the value
```
a = released["iphone 5"]
```
## mMethod
```
clear()
copy()
fromkeys(seq[, v])
get(key[,d])
items()
keys()
pop(key[,d]
popitem()
setdefault(key[,d])
update([other])
values()
```
