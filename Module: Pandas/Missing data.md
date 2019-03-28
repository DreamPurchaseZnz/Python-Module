# Working with missing data

## Detecting missing values easier
```
pandas.isna(obj)              ---> scalar or array like
pandas.notna(obj)

```

## Inserting missing data

You can insert missing values by simply assigning to containers


## Calculations with missing data

When summing data, NA (missing) values will be treated as zero

```
NaN + 0.01 = NaN  
sum([NaN, 0.1]) = 0.1
```

## NA values in GroupBy
```
In [153]: data = pd.Series(np.random.randn(100))

In [154]: factor = pd.qcut(data, [0, .25, .5, .75, 1.])

In [155]: data.groupby(factor).mean()
Out[155]: 
(-2.618, -0.684]    -1.331461
(-0.684, -0.0232]   -0.272816
(-0.0232, 0.541]     0.263607
(0.541, 2.369]       1.166038
dtype: float64
```

## Cleaning / filling missing data

### Filling missing values: fillna

Fill gaps forward or backward

```
DataFrame.fillna(
value=None,              ---> Dataframe
method=None,             ---> {‘backfill’, ‘bfill’, ‘pad’(forward), ‘ffill’(forward), None}, default None
axis=None,               ---> {0 or ‘index’, 1 or ‘columns’}
inplace=False,            
limit=None,              ---> the maximum number of consecutive NaN values to forward/backward fill
downcast=None, 
**kwargs)[source]
```
ffill() is equivalent to fillna(method='ffill') and bfill() is equivalent to fillna(method='bfill')

### Where
Return an object of same shape as self and 
whose corresponding entries are from self where cond is True and otherwise are from other
```
DataFrame.where(
cond, 
other=nan,
inplace=False,
axis=None, level=None, 
errors='raise', 
try_cast=False, 
raise_on_error=None
)
```
dff.fillna(dff.mean()) equal to the following
```
dff.where(pd.notna(dff), dff.mean(), axis='columns')
``` 

### Dropping axis labels with missing data: dropna
```
DataFrame.dropna(
axis=0,                           ---> {0 or ‘index’, 1 or ‘columns’}, default 0 
how='any',                        ---> {‘any’, ‘all’}, default ‘any’ 
                                       when we have at least one NA or all NA
thresh=None, 
subset=None, 
inplace=False)                    ---> If True, do operation inplace and return None
```

### Interpolation
```
DataFrame.interpolate(
method='linear',                  
axis=0, 
limit=None,                           ---> Maximum number of consecutive NaNs 
inplace=False, 
limit_direction='forward',            ---> {‘forward’, ‘backward’, ‘both’}, default ‘forward’
limit_area=None,                      ---> {‘inside’, ‘outside’}, default None 
downcast=None, 
**kwargs)
```
```
‘linear’               ---> ignore the index and treat the values as equally spaced. 
‘time’                 ---> interpolate given length of interval
‘index’, ‘values’      ---> use the actual numerical values of the index

‘nearest’, ‘zero’, ‘slinear’, ‘quadratic’, ‘cubic’, ‘barycentric’, ‘polynomial’ is passed to scipy.interpolate.interp1d. Both                                                                  ‘polynomial’ and ‘spline’ require that you also specify an order (int)

‘krogh’, ‘piecewise_polynomial’, ‘spline’, ‘pchip’ and ‘akima’ are all wrappers around the scipy interpolation methods 
                                                                see the scipy documentation and tutorial documentation
                                                                
‘from_derivatives’ refers to BPoly.from_derivatives which replaces ‘piecewise_polynomial’ interpolation method in scipy 0.18
```


### Replacing Generic Values

Replace values given in to_replace with value
```
Series.replace(
to_replace=None,      ---> str, regex, list, dict, Series, int, float, or None
value=None,  
inplace=False, 
limit=None, 
regex=False,
method='pad'          ---> {‘pad’, ‘ffill’, ‘bfill’, None}
)
```

### String/Regular Expression Replacement

Python strings prefixed with the r character such as r'hello world' are so-called “raw” strings. 

They have different semantics regarding backslashes than strings without this prefix. 

```
In [105]: d = {'a': list(range(4)), 'b': list('ab..'), 'c': ['a', 'b', np.nan, 'd']}

In [106]: df = pd.DataFrame(d)

In [107]: df.replace('.', np.nan)
Out[107]: 
   a    b    c
0  0    a    a
1  1    b    b
2  2  NaN  NaN
3  3  NaN    d

```
```

In [108]: df.replace(r'\s*\.\s*', np.nan, regex=True)
Out[108]: 
   a    b    c
0  0    a    a
1  1    b    b
2  2  NaN  NaN
3  3  NaN    d
```
### Numeric Replacement
```
In [118]: df = pd.DataFrame(np.random.randn(10, 2))

In [119]: df[np.random.rand(df.shape[0]) > 0.5] = 1.5

In [120]: df.replace(1.5, np.nan)
Out[120]: 
          0         1
0 -0.844214 -1.021415
1  0.432396 -0.323580
2  0.423825  0.799180
3  1.262614  0.751965
4       NaN       NaN
5       NaN       NaN
6 -0.498174 -1.060799
7  0.591667 -0.183257
8  1.019855 -1.482465
9       NaN       NaN
```

## Missing data casting rules and indexing

While pandas supports storing arrays of integer and boolean type, these types are not capable of storing missing data. Until we can switch to using a native NA type in NumPy, we’ve established some “casting rules”.


