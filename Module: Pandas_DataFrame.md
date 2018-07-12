# [Pandas.Series](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.html)

One-dimensional ndarray with axis labels (including time series)

```
class pandas.Series(
data=None, 
index=None, 
dtype=None, 
name=None, 
copy=False, 
fastpath=False
)
```
## Attribute
```
T
asobject
at
axes
base
blocks
data
dtype
dtypes
flags
ftype
ftypes
hasnans
iat
iloc
index
is_monotonic
is_monotonic_decreasing
is_monotonic_increasing
is_unique
itemsize
ix
loc
nbytes
ndim
shape
size
strides
values
empty
imag
is_copy
name
real
```
## Methods
```
abs()
add(other[, level, fill_value, axis])
add_prefix(prefix)
add_suffix(suffix)
agg(func[, axis])
aggregate(func[, axis])
align(other[, join, axis, level, copy, …])
all([axis, bool_only, skipna, level])
any([axis, bool_only, skipna, level])
append(to_append[, ignore_index, …])
apply(func[, convert_dtype, args])
argmax([axis, skipna])
argmin([axis, skipna])
argsort([axis, kind, order])
as_blocks([copy])
as_matrix([columns])
asfreq(freq[, method, how, normalize, …])
asof(where[, subset])
astype(dtype[, copy, errors])
at_time(time[, asof])
autocorr([lag])
between(left, right[, inclusive])
between_time(start_time, end_time[, …])
bfill([axis, inplace, limit, downcast])
bool()
cat
clip([lower, upper, axis, inplace])
clip_lower(threshold[, axis, inplace])
clip_upper(threshold[, axis, inplace])
combine(other, func[, fill_value])
combine_first(other)
compound([axis, skipna, level])
compress(condition, *args, **kwargs)
consolidate([inplace])
convert_objects([convert_dates, …])
copy([deep])
corr(other[, method, min_periods])
count([level])
cov(other[, min_periods])
cummax([axis, skipna])
cummin([axis, skipna])
cumprod([axis, skipna])
cumsum([axis, skipna])
describe([percentiles, include, exclude])
diff([periods])
div(other[, level, fill_value, axis])
divide(other[, level, fill_value, axis])
divmod(other[, level, fill_value, axis])
dot(other)
drop([labels, axis, index, columns, level, …])
drop_duplicates([keep, inplace])
dropna([axis, inplace])
dt
duplicated([keep])
eq(other[, level, fill_value, axis])
equals(other)
ewm([com, span, halflife, alpha, …])
expanding([min_periods, center, axis])
factorize([sort, na_sentinel])
ffill([axis, inplace, limit, downcast])
fillna([value, method, axis, inplace, …])
filter([items, like, regex, axis])
first(offset)
first_valid_index()
floordiv(other[, level, fill_value, axis])
from_array(arr[, index, name, dtype, copy, …])
from_csv(path[, sep, parse_dates, header, …])
ge(other[, level, fill_value, axis])
get(key[, default])
get_dtype_counts()
get_ftype_counts()
get_value(label[, takeable])
get_values()
groupby([by, axis, level, as_index, sort, …])
gt(other[, level, fill_value, axis])
head([n])
hist([by, ax, grid, xlabelsize, xrot, …])
idxmax([axis, skipna])
idxmin([axis, skipna])
infer_objects()
interpolate([method, axis, limit, inplace, …])
isin(values)
isna()
isnull()
item()
items()
iteritems()
keys()
kurt([axis, skipna, level, numeric_only])
kurtosis([axis, skipna, level, numeric_only])
last(offset)
last_valid_index()
le(other[, level, fill_value, axis])
lt(other[, level, fill_value, axis])
mad([axis, skipna, level])
map(arg[, na_action])
mask(cond[, other, inplace, axis, level, …])
max([axis, skipna, level, numeric_only])
mean([axis, skipna, level, numeric_only])
median([axis, skipna, level, numeric_only])
memory_usage([index, deep])
min([axis, skipna, level, numeric_only])
mod(other[, level, fill_value, axis])
mode()
mul(other[, level, fill_value, axis])
multiply(other[, level, fill_value, axis])
ne(other[, level, fill_value, axis])
nlargest([n, keep])
nonzero()
notna()
notnull()
nsmallest([n, keep])
nunique([dropna])
pct_change([periods, fill_method, limit, freq])
pipe(func, *args, **kwargs)
plot
pop(item)
pow(other[, level, fill_value, axis])
prod([axis, skipna, level, numeric_only, …])
product([axis, skipna, level, numeric_only, …])
ptp([axis, skipna, level, numeric_only])
put(*args, **kwargs)
quantile([q, interpolation])
radd(other[, level, fill_value, axis])
rank([axis, method, numeric_only, …])
ravel([order])
rdiv(other[, level, fill_value, axis])
reindex([index])
reindex_axis(labels[, axis])
reindex_like(other[, method, copy, limit, …])
rename([index])
rename_axis(mapper[, axis, copy, inplace])
reorder_levels(order)
repeat(repeats, *args, **kwargs)
replace([to_replace, value, inplace, limit, …])
resample(rule[, how, axis, fill_method, …])
reset_index([level, drop, name, inplace])
rfloordiv(other[, level, fill_value, axis])
rmod(other[, level, fill_value, axis])
rmul(other[, level, fill_value, axis])
rolling(window[, min_periods, center, …])
round([decimals])
rpow(other[, level, fill_value, axis])
rsub(other[, level, fill_value, axis])
rtruediv(other[, level, fill_value, axis])
sample([n, frac, replace, weights, …])
searchsorted(value[, side, sorter])
select(crit[, axis])
sem([axis, skipna, level, ddof, numeric_only])
set_axis(labels[, axis, inplace])
set_value(label, value[, takeable])
shift([periods, freq, axis])
skew([axis, skipna, level, numeric_only])
slice_shift([periods, axis])
sort_index([axis, level, ascending, …])
sort_values([axis, ascending, inplace, …])                       ---> sort by values
sortlevel([level, ascending, sort_remaining])
squeeze([axis])
std([axis, skipna, level, ddof, numeric_only])
str
sub(other[, level, fill_value, axis])
subtract(other[, level, fill_value, axis])
sum([axis, skipna, level, numeric_only, …])
swapaxes(axis1, axis2[, copy])
swaplevel([i, j, copy])
tail([n])
take(indices[, axis, convert, is_copy])
to_clipboard([excel, sep])
to_csv([path, index, sep, na_rep, …])
to_dense()
to_dict([into])
to_excel(excel_writer[, sheet_name, na_rep, …])
to_frame([name])
to_hdf(path_or_buf, key, **kwargs)
to_json([path_or_buf, orient, date_format, …])
to_latex([buf, columns, col_space, header, …])
to_msgpack([path_or_buf, encoding])
to_period([freq, copy])
to_pickle(path[, compression, protocol])
to_sparse([kind, fill_value])
to_sql(name, con[, schema, if_exists, …])
to_string([buf, na_rep, float_format, …])
to_timestamp([freq, how, copy])
to_xarray()
tolist()
transform(func, *args, **kwargs)
transpose(*args, **kwargs)
truediv(other[, level, fill_value, axis])
truncate([before, after, axis, copy])
tshift([periods, freq, axis])
tz_convert(tz[, axis, level, copy])
tz_localize(tz[, axis, level, copy, ambiguous])
unique()
unstack([level, fill_value])
update(other)
valid([inplace])
value_counts([normalize, sort, ascending, …])
var([axis, skipna, level, ddof, numeric_only])
view([dtype])
where(cond[, other, inplace, axis, level, …])
xs(key[, axis, level, drop_level])

```

# Module: [Pandas.DataFrame](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html)
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
at                                 ---> Acess a single value for row/column label pair         
axes                               ---> Return a list with the row axis labels 
                                        and column axis labels as the only members.
blocks              
dtypes              
empty              
ftypes              
iat                                ---> integer position compared with at
iloc                                           
is_copy              
ix              
loc                               ---> Access a group of rows and columns by label(s) or a boolean array           
ndim                              ---> Number of axes / array dimensions
shape                             ---> Return a tuple representing the dimensionality of the DataFrame.
size                              ---> Number of elements in the NDFrame
style              
values              
```

## Method
```
abs()
add(other[, axis, level, fill_value])
add_prefix(prefix)
add_suffix(suffix)
agg(func[, axis])
aggregate(func[, axis])
align(other[, join, axis, level, copy, …])
all([axis, bool_only, skipna, level])
any([axis, bool_only, skipna, level])
append(other[, ignore_index, …])                     ---> append Rows of the other              
apply(func[, axis, broadcast, raw, reduce, …])       ---> apply a function along an axis
applymap(func)
as_blocks([copy])
as_matrix([columns])
asfreq(freq[, method, how, normalize, …])
asof(where[, subset])
assign(**kwargs)                                    ---> assign new columns to Dataframe
astype(dtype[, copy, errors])
at_time(time[, asof])
between_time(start_time, end_time[, …])
bfill([axis, inplace, limit, downcast])
bool()
boxplot([column, by, ax, fontsize, rot, …])         ---> Make a boxPlot from dataframe columns
clip([lower, upper, axis, inplace])                 
clip_lower(threshold[, axis, inplace])              ---> the input with values below a threshold truncated
clip_upper(threshold[, axis, inplace])              ---> input with values above given value(s) truncated.
combine(other, func[, fill_value, overwrite])       
combine_first(other)
compound([axis, skipna, level])
consolidate([inplace])
convert_objects([convert_dates, …])
copy([deep])
corr([method, min_periods])                         ---> Compute pairwise correlation of columns, 
                                                         excluding NA/null values
corrwith(other[, axis, drop])                       ---> Two DataFrame objects
count([axis, level, numeric_only])                  ---> Count non-NA cells for each column or row
cov([min_periods])                                  ---> Compute pairwise covariance of columns
cummax([axis, skipna])
cummin([axis, skipna])
cumprod([axis, skipna])
cumsum([axis, skipna])
describe([percentiles, include, exclude])
diff([periods, axis])                               ---> First discrete Difference
div(other[, axis, level, fill_value])
divide(other[, axis, level, fill_value])
dot(other)
drop([labels, axis, index, columns, level, …])      ---> Drop specified labels from rows or columns
drop_duplicates([subset, keep, inplace])
dropna([axis, how, thresh, subset, inplace])        ---> Remove missing values.
duplicated([subset, keep])
eq(other[, axis, level])
equals(other)
eval(expr[, inplace])
ewm([com, span, halflife, alpha, …])
expanding([min_periods, center, axis])
ffill([axis, inplace, limit, downcast])
fillna([value, method, axis, inplace, …])           ---> Fill NA/NaN values using the specified method
filter([items, like, regex, axis])
first(offset)
first_valid_index()
floordiv(other[, axis, level, fill_value])
from_csv(path[, header, sep, index_col, …])
from_dict(data[, orient, dtype, columns])
from_items(items[, columns, orient])
from_records(data[, index, exclude, …])
ge(other[, axis, level])
get(key[, default])
get_dtype_counts()
get_ftype_counts()
get_value(index, col[, takeable])
get_values()
groupby([by, axis, level, as_index, sort, …])       ---> Group series using mapper
gt(other[, axis, level])
head([n])
hist([column, by, grid, xlabelsize, xrot, …])
idxmax([axis, skipna])                              ---> Return index of first occurrence of maximum
idxmin([axis, skipna])
infer_objects()
info([verbose, buf, max_cols, memory_usage, …])     ---> Print a concise summary 
insert(loc, column, value[, allow_duplicates]) 
interpolate([method, axis, limit, inplace, …])
isin(values)
isna()
isnull()
items()
iteritems()
iterrows()
itertuples([index, name])
join(other[, on, how, lsuffix, rsuffix, sort])
keys()
kurt([axis, skipna, level, numeric_only])
kurtosis([axis, skipna, level, numeric_only])
last(offset)
last_valid_index()
le(other[, axis, level])
lookup(row_labels, col_labels)
lt(other[, axis, level])
mad([axis, skipna, level])
mask(cond[, other, inplace, axis, level, …])
max([axis, skipna, level, numeric_only])
mean([axis, skipna, level, numeric_only])          ---> Return the mean of the values for the requested axis
median([axis, skipna, level, numeric_only])
melt([id_vars, value_vars, var_name, …])
memory_usage([index, deep])
merge(right[, how, on, left_on, right_on, …])
min([axis, skipna, level, numeric_only])
mod(other[, axis, level, fill_value])
mode([axis, numeric_only])
mul(other[, axis, level, fill_value])
multiply(other[, axis, level, fill_value])
ne(other[, axis, level])
nlargest(n, columns[, keep])
notna()
notnull()
nsmallest(n, columns[, keep])
nunique([axis, dropna])
pct_change([periods, fill_method, limit, freq])
pipe(func, *args, **kwargs)
pivot([index, columns, values])
pivot_table([values, index, columns, …])
plot
pop(item)
pow(other[, axis, level, fill_value])
prod([axis, skipna, level, numeric_only, …])
product([axis, skipna, level, numeric_only, …])
quantile([q, axis, numeric_only, interpolation])
query(expr[, inplace])
radd(other[, axis, level, fill_value])
rank([axis, method, numeric_only, …])
rdiv(other[, axis, level, fill_value])
reindex([labels, index, columns, axis, …])
reindex_axis(labels[, axis, method, level, …])
reindex_like(other[, method, copy, limit, …])
rename([mapper, index, columns, axis, copy, …])        ---> Alter axes labels
rename_axis(mapper[, axis, copy, inplace])
reorder_levels(order[, axis])
replace([to_replace, value, inplace, limit, …])
resample(rule[, how, axis, fill_method, …])
reset_index([level, drop, inplace, …])
rfloordiv(other[, axis, level, fill_value])
rmod(other[, axis, level, fill_value])
rmul(other[, axis, level, fill_value])
rolling(window[, min_periods, center, …])             ---> Provides rolling window calculations.
round([decimals])
rpow(other[, axis, level, fill_value])
rsub(other[, axis, level, fill_value])
rtruediv(other[, axis, level, fill_value])
sample([n, frac, replace, weights, …])
select(crit[, axis])
select_dtypes([include, exclude])
sem([axis, skipna, level, ddof, numeric_only])
set_axis(labels[, axis, inplace])
set_index(keys[, drop, append, inplace, …])
set_value(index, col, value[, takeable])
shift([periods, freq, axis])
skew([axis, skipna, level, numeric_only])
slice_shift([periods, axis])
sort_index([axis, level, ascending, …])
sort_values(by[, axis, ascending, inplace, …])
sortlevel([level, axis, ascending, inplace, …])
squeeze([axis])
stack([level, dropna])
std([axis, skipna, level, ddof, numeric_only])
sub(other[, axis, level, fill_value])
subtract(other[, axis, level, fill_value])
sum([axis, skipna, level, numeric_only, …])
swapaxes(axis1, axis2[, copy])
swaplevel([i, j, axis])
tail([n])                                           ---> Return the last n rows.
take(indices[, axis, convert, is_copy])
to_clipboard([excel, sep])
to_csv([path_or_buf, sep, na_rep, …])               ---> Write DataFrame to a comma-separated values (csv) file
to_dense()
to_dict([orient, into])
to_excel(excel_writer[, sheet_name, na_rep, …])     ---> 	Write DataFrame to an excel sheet
to_feather(fname)
to_gbq(destination_table, project_id[, …])
to_hdf(path_or_buf, key, **kwargs)                  
to_html([buf, columns, col_space, header, …])       ---> Render a DataFrame as an HTML table
to_json([path_or_buf, orient, date_format, …])
to_latex([buf, columns, col_space, header, …])      ---> Render an object to a tabular environment table
to_msgpack([path_or_buf, encoding])
to_panel()
to_parquet(fname[, engine, compression])
to_period([freq, axis, copy])
to_pickle(path[, compression, protocol])            ---> Pickle (serialize) object to file
to_records([index, convert_datetime64])
to_sparse([fill_value, kind])
to_sql(name, con[, schema, if_exists, …])
to_stata(fname[, convert_dates, …])
to_string([buf, columns, col_space, header, …])
to_timestamp([freq, how, axis, copy])
to_xarray()
transform(func, *args, **kwargs)                    ---> Transpose index and columns
transpose(*args, **kwargs)
truediv(other[, axis, level, fill_value])
truncate([before, after, axis, copy])
tshift([periods, freq, axis])
tz_convert(tz[, axis, level, copy])
tz_localize(tz[, axis, level, copy, ambiguous])
unstack([level, fill_value])
update(other[, join, overwrite, …])
var([axis, skipna, level, ddof, numeric_only])
where(cond[, other, inplace, axis, level, …])
xs(key[, axis, level, drop_level])

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
## Read_excel
```
pandas.read_excel(
io,                             ---> string, path object (pathlib.Path or py._path.local.LocalPath)
sheet_name=0,                   ---> string, int, mixed list of strings/ints
header=0,                       ---> Row (0-indexed) to use for the column labels of the parsed DataFrame.
skiprows=None, 
skip_footer=0, 
index_col=None, 
names=None, 
usecols=None, 
parse_dates=False, 
date_parser=None, 
na_values=None, 
thousands=None,                   ---> Thousands separator for parsing string columns to numeric.
convert_float=True, 
converters=None, 
dtype=None, 
true_values=None, 
false_values=None, 
engine=None, 
squeeze=False, 
**kwds)
```



