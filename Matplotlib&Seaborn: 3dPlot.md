# [Mplot3d](https://matplotlib.org/tutorials/toolkits/mplot3d.html#sphx-glr-tutorials-toolkits-mplot3d-py)
- Line plots
- Scatter plots
- Wireframe plots
- Surface plots
- Tri-Surface plots
- Contour plots
- Filled contour plots
- Polygon plots
- Bar plots
- Quiver
- 2D plots in 3D
- Text
- Subplotting
```
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')

```
## Line plots

```
Axes3D.plot(
xs, ys,                         ---> x,y coordinates of indices 
*args, 
**kwargs)
```

## scatter plots
```
Axes3D.scatter(
xs, ys,                        ---> Positions of data points
zs=0,                          ---> single value or same shape as xs
zdir='z',                      ---> which direction plots the 2D  
s=20,                          ---> Single value or same length
c=None, 
depthshade=True, 
*args, **kwargs
)

```
## Surface plots
Create a surface plot
```
Axes3D.plot_surface(
X, Y, Z                       ---> 2d arrays
rcount, ccount                ---> int
rstride, cstride              ---> int
cmap                          ---> Colormap
color                         ---> Color of the surface patches
facecolors                    ---> Colors of each individual patch
norm 
vmin, vmax
shade                         ---> Whether to shade the face colors
*args, 
**kwargs)

```
![surface_plot](https://matplotlib.org/_images/sphx_glr_surface3d_001.png)


# [Seaborn](http://seaborn.pydata.org/index.html)
## [sns.cubehelix_palette](http://seaborn.pydata.org/generated/seaborn.cubehelix_palette.html)
Make a sequential palette from cubhelix system

This produces a colormap with linearly-increasing brightness, which means that information will be
preserved if printed to black and white or viewed by someone who is colorblind.
```
seaborn.cubehelix_palette(
n_colors=6,                                ---> number of colors in the palette
start=0,                                   ---> the hue at the start of helix
rot=0.4,                                   
gamma=1.0, 
hue=0.8, 
light=0.85, 
dark=0.15,
reverse=False, 
as_cmap=False
)
```
## [sns.distplot](http://seaborn.pydata.org/generated/seaborn.distplot.html)
Flexibly plot a univariate distribution of observations
conbines:
- matplotlib *hist* function
- seaborn *kdeplot* and *rugplot*
- *scipy.stats* distribution for estimate PDF over data

```
seaborn.distplot(
a,                           ---> Series, 1d-array or list
bins=None,                   ---> Specification of hist bins
hist=True,                   ---> Whether to plot a histogram
kde=True,                    ---> Whether to plot a gaussian kernel density estimate
rug=False,                   ---> Whether to plot a rugplot on the support axis
fit=None,                    ---> Returning a tupe can be passed to a pdf method
hist_kws=None,               ---> Keywords for underlying plotting functions
kde_kws=None, 
rug_kws=None, 
fit_kws=None, 
color=None, 
vertical=False, 
norm_hist=False,             ---> If true, the histogram shows a density rather than a count
axlabel=None,                ---> The support axis label
label=None,                  ---> Legend label for the relevent components of the plot
ax=None                      ---> if provided, plot on this axis
)
```

## [sns.kdeplot](http://seaborn.pydata.org/generated/seaborn.kdeplot.html)
Fit and plot a univariate or bivariate kernel density estimate
```
seaborn.kdeplot(
data,                   ---> 1d array-like
data2=None,             ---> if present, a bivariate KDE will be estimated
shade=False,            ---> if True, shade in the area under KDE curve (or draw with filled contours when data is bivariate)
vertical=False,         ---> if True, density is on x axis
kernel='gau',           ---> bivariate kde can only use gaussian kernel 
bw='scott',             ---> {‘scott’ | ‘silverman’ | scalar | pair of scalars }, optional
gridsize=100,           ---> number of discrete points in evaluation grid
cut=3,                  ---> Draw the estimate to cut * bw from the extreme data points.                 
clip=None,              ---> Lower and upper bounds for datapoints used to fit KDE
legend=True, 
cumulative=False, 
shade_lowest=True, 
cbar=False,             ---> add a colorbar 
cbar_ax=None, 
cbar_kws=None, 
ax=None, 
**kwargs)
```
![kdeplot](http://seaborn.pydata.org/_images/seaborn-kdeplot-10.png)


## sns.jointplot

```
seaborn.jointplot(
x,  y,                                       ---> Data or name of variables in data
data=None,                                   ---> DataFrame
kind='scatter',                              ---> { “scatter” | “reg” | “resid” | “kde” | “hex” }, optional
stat_func=<function pearsonr>,               ---> annotate the plot with a (value , p)
color=None, 
size=6,                                      ---> size of the features
ratio=5,                                     ---> axis size to marginal axes height
space=0.2,                                   ---> space between the joint and marginal axes
dropna=True,                                 ---> drop Na
xlim=None, 
ylim=None,
joint_kws=None,                              ---> additional keyword arguments for the plot components
marginal_kws=None, 
annot_kws=None, 
**kwargs)
```














