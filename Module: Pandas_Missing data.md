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




