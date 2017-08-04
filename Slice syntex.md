Slice syntex: Colon':'
======
## Colon':'
: is the delimiter of the slice syntax to 'slice out' sub-parts in sequences , [start:end]

It's pretty simple really:
```
a[start:end] # items start through end-1
a[start:]    # items start through the rest of the array
a[:end]      # items from the beginning through end-1
a[:]         # a copy of the whole array
```
There is also the step value, which can be used with any of the above:
```
a[start:end:step] # start through not past end, by step
```
The key point to remember is that the :end value represents the first value that is not in the **selected slice**. So, the difference beween end and start is the number of elements selected (if step is 1, the default).

The other feature is that start or end may be a negative number, which means it counts **from the end of the array** instead of the beginning. So:
```
a[-1]    # last item in the array
a[-2:]   # last two items in the array
a[:-2]   # everything except the last two items
```
Python is kind to the programmer if there are fewer items than you ask for. For example, if you ask for a[:-2] and a only contains one element, you get an empty list instead of an error. Sometimes you would prefer the error, so you have to be aware that this may happen.


```
>>> seq[:]                # [seq[0],   seq[1],          ..., seq[-1]    ]
>>> seq[low:]             # [seq[low], seq[low+1],      ..., seq[-1]    ]
>>> seq[:high]            # [seq[0],   seq[1],          ..., seq[high-1]]
>>> seq[low:high]         # [seq[low], seq[low+1],      ..., seq[high-1]]
>>> seq[::stride]         # [seq[0],   seq[stride],     ..., seq[-1]    ]
>>> seq[low::stride]      # [seq[low], seq[low+stride], ..., seq[-1]    ]
>>> seq[:high:stride]     # [seq[0],   seq[stride],     ..., seq[high-1]]
>>> seq[low:high:stride]  # [seq[low], seq[low+stride], ..., seq[high-1]]                                   
```

## '/','./','../'
```
/   -Root directory
./  -current working directory 
../ -parent directory, respectively
```
