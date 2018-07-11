# Module: Pandas.DataFrame
----------------------------------------------------------------------------------------------------------------
Two-dimensional size-mutable, potentially heterogenious tabular data structure with labeled axes(rows and columns)
Arithmetic operation align on both row and column lables ,can be thought of dict_like container for series objects
The primary pandas data structure.
```
class pandas.DataFrame(data=None, index=None, columns=None, dtype=None, copy=False)
```
```
data                               ---> Numpy ndarray (structured or homogeneous), dict, or DataFrame
                                        Dict can contain Series, arrays, constants, or list-like objects
index                              ---> Row index, default to np.arange(n)
columns                            ---> Columns index
dtype                              ---> Data type to force otherwise infer
copy                               ---> Boolean ,default False
```
```
import pandas as pd
Backend Qt5Agg is interactive backend. Turning interactive mode on.
import numpy as np

df = pd.DataFrame(np.random.randn(5, 3), 
                  index=['a', 'c', 'e', 'f', 'h'],
                  columns=['one', 'two', 'three'])

df: 
        one       two     three
a  1.321618  0.020105 -1.177809
c -0.136758  1.216013  1.209642
e  0.211499 -0.188715  0.307192
f  0.059934 -0.375001 -0.568702
h  0.400770  0.223357  0.744262


```


**Attributes**
```
T                                  ---> Transpose index and columns
at              
axes                               ---> Return a list with the row axis labels 
                                        and column axis labels as the only members.
blocks              
dtypes              
empty              
ftypes              
iat              
iloc              
is_copy              
ix              
loc              
ndim                              ---> Number of axes / array dimensions
shape                             ---> Return a tuple representing the dimensionality of the DataFrame.
size                              ---> Number of elements in the NDFrame
style              
values              
```

## pandas.read_csv
Read CSV (comma-separated) file into DataFrame
```
pandas.read_csv(
filepath_or_buffer, 
sep=', ', 
delimiter=None, 
header='infer',
names=None, 
index_col=None, 
usecols=None, 
squeeze=False, 
prefix=None, 
mangle_dupe_cols=True, 
dtype=None, 
engine=None, 
converters=None, 
true_values=None,
false_values=None, 
skipinitialspace=False, 
skiprows=None, 
nrows=None, 
na_values=None, 
keep_default_na=True,                  ---> Whether or not to include the default NaN 
                                            values when parsing the data
na_filter=True, 
verbose=False, 
skip_blank_lines=True,                 ---> If True, skip over blank lines rather 
                                            than interpreting as NaN values
parse_dates=False, 
infer_datetime_format=False, 
keep_date_col=False,
date_parser=None, 
dayfirst=False, 
iterator=False, 
chunksize=None, 
compression='infer', 
thousands=None, 
decimal=b'.', 
lineterminator=None, 
quotechar='"', 
quoting=0, 
escapechar=None, 
comment=None, 
encoding=None, 
dialect=None, 
tupleize_cols=None,
error_bad_lines=True, 
warn_bad_lines=True, 
skipfooter=0, 
doublequote=True,
delim_whitespace=False, 
low_memory=True, 
memory_map=False, 
float_precision=None)
```
```
Return 
DataFrame or TextParser
```





