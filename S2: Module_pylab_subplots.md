# Subplots
Create a figure and a set of subplots
This utility wrapper makes it convenient to create common layouts of subplots
```
matplotlib.pyplot.subplots(
nrows=1, 
ncols=1,              --->  int, optional, default: 1
sharex=False,         --->  bool or {‘none’, ‘all’, ‘row’, ‘col’}
sharey=False, 
squeeze=True, 
subplot_kw=None, 
gridspec_kw=None,     --->  figure() call below
**fig_kw)
```
Return
```
fig
ax
```
Creates just a figure and only one subplot
```
fig,ax = plt.subplots()

```
Creates two subplots and unpacks the output array immediately
```
fig, (ax1,ax2) = plt.subplots(1,2, sharey=True)

```
Creates four subplots and acesses them through the returned way
```
fig, axes = plt.subplots(2,2, sbuplot_kw=dict(polar=True))
axe[0,0].plot(x,y)
```
## matplotlib.pyplot.subplot
Return a subplot axes positioned by the given grid definition.
Typical call signature:
```
subplot(nrows,
ncols,
plot_number)
```
## matplotlib.pyplot.subplot2grid
```
subplot2grid(
shape,
loc,
rowspan=1, 
colspan=1, 
**kwargs)
```
Create a subplot in a grid. The grid is specified by shape, at location of loc, spanning rowspan, colspan cells in each direction. The index for loc is 0-based.

identical to:
```
gridspec=GridSpec(shape[0], shape[1])
subplotspec=gridspec.new_subplotspec(loc, rowspan, colspan)
subplot(subplotspec)
```

## gridspec
gridspec is a module which specifies the location of the subplot in the figure

```
class matplotlib.gridspec.GridSpec(
nrows, 
ncols, 
left=None, 
bottom=None, 
right=None, 
top=None, 
wspace=None, 
hspace=None, 
width_ratios=None, 
height_ratios=None)

```
[a good explanation here](https://matplotlib.org/users/gridspec.html?highlight=gridspec)
I just post it. Maybe after some days or months ,i will review it 



# figure()
```
matplotlib.pyplot.figure(
num=None,                        ---> integer or string, optional, default: none :number attribute
figsize=None,                    ---> tuple of integer,(weight,heigt) units:inches
dpi=None,                        ---> resolution of figure
facecolor=None,                  ---> the background color 
edgecolor=None,                  ---> border color
frameon=True, 
FigureClass=<class 'matplotlib.figure.Figure'>,
**kwargs)
```
return
```
figure                          ---> The Figure instance returned will
                                     also be passed to new_figure_manager in the backends
```


# Set The Color Of A Matplotlib Plot
## show matplotlib colormaps
```
Toggle line numbers
from pylab import *
from numpy import outer
rc('text', usetex=False)
a=outer(arange(0,1,0.01),ones(10))
figure(figsize=(10,5))
subplots_adjust(top=0.8,bottom=0.05,left=0.01,right=0.99)
maps=[m for m in cm.datad if not m.endswith("_r")]
maps.sort()
l=len(maps)+1
for i, m in enumerate(maps):
     subplot(1,l,i+1)
     axis("off")
     imshow(a,aspect='auto',cmap=get_cmap(m),origin="lower")
     title(m,rotation=90,fontsize=10)
savefig("colormaps.png",dpi=100,facecolor='gray')
```
[Full list of colormaps:](http://wiki.scipy.org/Cookbook/Matplotlib/Show_colormaps)

```
%matplotlib inline
import numpy as np
import matplotlib.pyplot as plt
```
Create some simulated data
```
n = 100
r = 2 * np.random.rand(n)
theta = 2 * np.pi * np.random.rand(n)
area = 200 * r**2 * np.random.rand(n)
colors = theta
```
```
c = plt.scatter(theta, r, c=colors, s=area, cmap=plt.cm. RdY1Gn)
```
```
c1 = plt.scatter(theta, r, c=colors, s=area, cmap=plt.cm.Blues)

```
c = colors           ---> the object will be normalize the colors with "norm" method
```
colors.min()
Out[27]: 
0.017732887169740141
colors.max()
Out[28]: 
6.2816469274617965
```
s = area             ---> size in point^2
```
area.min()
Out[29]: 
0.046319677778216668
area.max()
Out[30]: 
617.85340922435944

```


















