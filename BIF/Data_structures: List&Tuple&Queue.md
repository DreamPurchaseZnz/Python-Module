# [Data Structures](https://docs.python.org/3.5/tutorial/datastructures.html)
## Tuple and list 
There are little difference between lists and tuples.
```
tuple/list[number]                # access the value at postion number
tuple/list + tuple/list           # concatenation
tuple/list * 3                    # repetation
```
## Tuple
A tuple is a sequence of immutable  python objects. Tuple are sequences, just like the lists. The difference between lists and tuples
are, tuples cannot be changed unlike the lists and tuples  use parentheses, whereas lists use the square bracks.
```
tup1 = ('physics', 'chemistry', 1997, 2000);
tup2 = (1, 2, 3, 4, 5 );
tup3 = "a", "b", "c", "d";
```


### accessing the values of the tuple 
use the square bracks for slicing along the axis.
```
tup1 = ('physics', 'chemistry', 1997, 2000);
tup2 = (1, 2, 3, 4, 5, 6, 7 );
print "tup1[0]: ", tup1[0];
print "tup2[1:5]: ", tup2[1:5];
```
As you can see, tuple cannot be changed, but you are able to take portions of the existing tuples to create a new one.
```
tup1 = (12, 34.56);
tup2 = ('abc', 'xyz');

# Following action is not valid for tuples
# tup1[0] = 100;

# So let's create a new tuple as follows
tup3 = tup1 + tup2;
print tup3;
```
### basic tuple operations
Tuple respond to the + and * operators  much like strings; they mean concatenation and repetition here too, except the result is 
a new tuple not a string.

```
Python                      Expression	Results                       Description
len((1, 2, 3))	               3	                                       Length
(1, 2, 3) + (4, 5, 6)      	(1, 2, 3, 4, 5, 6)	                      Concatenation
('Hi!',) * 4	             ('Hi!', 'Hi!', 'Hi!', 'Hi!')	                Repetition
3 in (1, 2, 3)	                   True	                                 Membership
for x in (1, 2, 3): print x,	    1 2 3	                                 Iteration
```

```
c = (1, 2, 3)                      # tuple
c[1]
2
c * 3
(1, 2, 3, 1, 2, 3, 1, 2, 3)
c = [1, 2, 3]                      # list
c * 3
[1, 2, 3, 1, 2, 3, 1, 2, 3]
```

### functions
```
cmp(tuple1, tuple2)               # Compares elements of both tuples.
len(tuple)                        # Gives the total length of the tuple.
max(tuple)                        # Returns item from the tuple with max value.
min(tuple)                        # Returns item from the tuple with min value.
tuple(seq)                        # Converts a list into tuple.
```


## 0. List

All of the methods of list objects
```
append                                   ---> Add an item to the end of the list
extend                                   ---> Extend the list by appending all the items in the given list
insert                                   ---> Insert an item at a given position 
remove                                   ---> Remove the first item from the list whose value is x
pop                                      ---> Remove the item at the given position in the list, and return it
index                                    ---> Return the index in the list of the first item whose value is x
count                                    ---> Return the number of times x appears in the list
sort                                     ---> Sort the items of the list in place
reverse                                  ---> Reverse the elements of the list, in place
```
```
a = [1,3,5,7,9]
a.pop()          # 9
a                # [1, 3, 5, 7]
a.append(9)      # [1, 3, 5, 7, 9]
a.extend([11,13])# [1, 3, 5, 7, 9, 11, 13]
a.pop()          # 13
a.pop()          # 11
a                # [1, 3, 5, 7, 9]
a.remove(1)      # [3, 5, 7, 9]
a.insert(1, 4)   # [3, 4, 5, 7, 9]
a.index(4)       # 1
a.count(4)       # 1
a.sort()         # [3, 4, 5, 7, 9]
a.reverse()      # [9, 7, 5, 4, 3]
```
### append Vs extend
**append**:
add an item to the end of the list; equivalent to a[len(a):]=[x]
```
x = [1,2,3]
x.append([4,5])     # [1, 2, 3, [4, 5]]
x = [1,2,3]
x[len(x):]=[4]      # [1, 2, 3, 4]
```

**extend**
list.extend(seq)- This method does not return any value but add the content to existing list

Extend the list by appending all the items in the given list; equivalent to a[len(a):] = L
```
x.extend([4,5])                 # [1, 2, 3, [4, 5], 4, 5]
x[len(x):]=[4,5]                # [1, 2, 3, 4, 4, 5]
aList = [123, 'xyz', 
'zara', 'abc', 123];
bList = [2009, 'manni'];
aList.extend(bList)             # [123, 'xyz', 'zara', 'abc', 123, 2009, 'manni']
```
when it comes to the numpy array, the append/extend method can't be used to append/extend
it by attribute.
```
import numpy as np
c['e'].append(np.array([1,2]))  # [array([1, 2])]
c['e'].append(np.array([1,2]))  # [array([1, 2]), array([1, 2])]
c['e'][1]                       # array([1, 2])
c['e'][1].append([4,5])
AttributeError: 'numpy.ndarray' object has no attribute 'append'
```
np.append method can be used for this situation
```
c['e'][1]=np.append(4, c['e'][1])       # array([4, 1, 2])
c['e'][1]=np.append(c['e'][1],[4,5])    # array([4, 1, 2, 4, 5])
```

## 1. More on Lists
```



```
```
>>> fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
>>> fruits.count('apple')
2
>>> fruits.count('tangerine')
0
>>> fruits.index('banana')
3
>>> fruits.index('banana', 4)  # Find next banana starting a position 4
6
>>> fruits.reverse()
>>> fruits
['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange']
>>> fruits.append('grape')
>>> fruits
['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange', 'grape']
>>> fruits.sort()
>>> fruits
['apple', 'apple', 'banana', 'banana', 'grape', 'kiwi', 'orange', 'pear']
>>> fruits.pop()
'pear'


```
## Using lists as Stacks
```



```

## Using lists as Queues
```



```
# Queue
The queue module implements multi-producer, multi-consumer queues; It is especially useful in threaded 
programming when information must be exchanged safely between multiple threads.
```
FIFO       ---> first input, first output
LIFO       ---> last input, first output
```
```
queue.Queue(maxsize=0)
queue.LifoQueue(maxsize=0)
queue.PriorityQueue(maxsize=0)
queue.Empty
queue.Full
```
## Queue Objects
```
Queue.qsize()

Queue.empty()              ---> Return True

Queue.full()               ---> Return True

Queue.put(
item,                      ---> Put item into queue
block=True, 
timeout=None
)
Queue.get(block=True, timeout=None)
Queue.join()
```

# Tuple
```
(2, 3) + (1, )
Out[2]: 
(2, 3, 1)
(2, 3) + (1, 2)
Out[3]: 
(2, 3, 1, 2)

```








