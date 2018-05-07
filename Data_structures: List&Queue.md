# [Data Structures](https://docs.python.org/3.5/tutorial/datastructures.html)
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









