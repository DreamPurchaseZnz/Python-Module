# Area
## Axes.fill(*args, data=None, **kwargs)[source]
```
ax.fill(x, y)                    # a polygon with default color
ax.fill(x, y, "b")               # a blue polygon
ax.fill(x, y, x2, y2)            # two polygons
ax.fill(x, y, "b", x2, y2, "r")  # a blue and a red polygon
```

## matplotlib.axes.Axes.fill_between
Fill the area between two horizontal curves.

The curves are defined by the points (x, y1) and (x, y2). This creates one or multiple polygons describing the filled area.

You may exclude some horizontal sections from filling using where.

By default, the edges connect the given points directly. Use step if the filling should be a step function, i.e. constant in between x.

```
x : array (length N)
The x coordinates of the nodes defining the curves.

y1 : array (length N) or scalar
The y coordinates of the nodes defining the first curve.

y2 : array (length N) or scalar, optional, default: 0
The y coordinates of the nodes defining the second curve.

where : array of bool (length N), optional, default: None

alpha:	float or None
color: color
```











## matplotlib.pyplot.stackplot
Draw a stacked area plot
```
matplotlib.pyplot.stackplot(x, *args, data=None, **kwargs)

x : 1d array of dimension N
y : 2d array (dimension MxN), or sequence of 1d arrays (each dimension 1xN)
```

The data is assumed to be unstacked. Each of the following calls is legal:
```
stackplot(x, y)               # where y is MxN
stackplot(x, y1, y2, y3, y4)  # where y1, y2, y3, y4, are all 1xNm
```
baseline : {'zero', 'sym', 'wiggle', 'weighted_wiggle'}
Method used to calculate the baseline:
```
'zero': Constant zero baseline, i.e. a simple stacked plot.
'sym': Symmetric around zero and is sometimes called 'ThemeRiver'.
'wiggle': Minimizes the sum of the squared slopes.
'weighted_wiggle': Does the same but weights to account for size of each layer. It is also called 'Streamgraph'-layout. More details can be found at http://leebyron.com/streamgraph/.
labels : Length N sequence of strings
Labels to assign to each data series.
```

colors : Length N sequence of colors
A list or tuple of colors. These will be cycled through and used to colour the stacked areas.

**kwargs :
All other keyword arguments are passed to Axes.fill_between().

Returns:	
```
list : list of PolyCollection
A list of PolyCollection instances, one for each element in the stacked area plot.
````
