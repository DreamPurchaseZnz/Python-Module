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
append:
add an item to the end of the list; equivalent to a[len(a):]=[x]
```
x = [1,2,3]
x.append([4,5])
print(x)
Out[14]: 
[1, 2, 3, [4, 5]]
```
```
x = [1,2,3]
x[len(x):]=[4]
x
Out[25]: 
[1, 2, 3, 4]

```

list.extend(seq)- This method does not return any value but add the content to existing list

Extend the list by appending all the items in the given list; equivalent to a[len(a):] = L
```
x.extend([4,5])
x
Out[18]: 
[1, 2, 3, [4, 5], 4, 5]
```
```
x[len(x):]=[4,5]
x
Out[28]: 
[1, 2, 3, 4, 4, 5]

```

```
aList = [123, 'xyz', 'zara', 'abc', 123];
bList = [2009, 'manni'];
aList.extend(bList)
aList
Out[20]: 
[123, 'xyz', 'zara', 'abc', 123, 2009, 'manni']

```
when it comes to the numpy array, the append/extend method can't be used to append/extend
it by attribute.
```
import numpy as np
c['e'].append(np.array([1,2]))
c['e']
Out[16]: 
[array([1, 2])]
c['e'].append(np.array([1,2]))
c['e']
Out[18]: 
[array([1, 2]), array([1, 2])]
c['e'][1]
Out[19]: 
array([1, 2])
c['e'][1].append([4,5])
AttributeError: 'numpy.ndarray' object has no attribute 'append'
```
np.append method can be used for this situation
```
c['e'][1]=np.append(4, c['e'][1])
c['e'][1]
Out[23]: 
array([4, 1, 2])
c['e'][1]=np.append(c['e'][1],[4,5])
c['e'][1]
Out[25]: 
array([4, 1, 2, 4, 5])


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
