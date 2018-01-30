# [Matplotlib.figure](https://matplotlib.org/api/figure_api.html)
```
AxesStack
Figure([figsize, dpi, facecolor, edgecolor, …])
SubplotParams([left, bottom, right, top, …])
```
## Figure
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
## Method of matplotlib.figure.Figure
```
add_subplot(*args, **kwargs)
clear(keep_observers=False)
clf(keep_observers=False)
colorbar(mappable, cax=None, ax=None, use_gridspec=True, **kw)
contains(mouseevent)
gca(**kwargs)                   ---> Get the current axes, creating one if necessary
ginput(n=1, timeout=30, show_clicks=True, mouse_add=1, mouse_pop=3, mouse_stop=2)
legend(*args, **kwargs)
savefig(fname, **kwargs)
subplots(nrows=1, ncols=1, sharex=False, sharey=False, squeeze=True, subplot_kw=None, gridspec_kw=None)
text(x, y, s, *args, **kwargs)
tight_layout(renderer=None, pad=1.08, h_pad=None, w_pad=None, rect=None)
waitforbuttonpress(timeout=-1)
```
```
savefig(fname, dpi=None, facecolor='w', edgecolor='w',
        orientation='portrait', papertype=None, format=None,
        transparent=False, bbox_inches=None, pad_inches=0.1,
        frameon=None)
```




## Subplots
Create a figure and a set of subplots
This utility wrapper makes it convenient to create common layouts of subplots
```
matplotlib.pyplot.subplots(
nrows=1, 
ncols=1,                                   --->  int, optional, default: 1
sharex=False,                              --->  bool or {‘none’, ‘all’, ‘row’, ‘col’}
sharey=False, 
squeeze=True, 
subplot_kw=None, 
gridspec_kw=None,                          --->  figure() call below
```
Return : fig, ax
```
f, axes = plt.subplots(3, 3, figsize=(9, 9), sharex=True, sharey=True)
```
when the above code is executed, the result is as follow:
```
axes
output:
array([[<matplotlib.axes._subplots.AxesSubplot object at 0x000000001CDCB080>,
        <matplotlib.axes._subplots.AxesSubplot object at 0x00000000191F15C0>,
        <matplotlib.axes._subplots.AxesSubplot object at 0x000000001BFB5518>],
       [<matplotlib.axes._subplots.AxesSubplot object at 0x000000001BCA95F8>,
        <matplotlib.axes._subplots.AxesSubplot object at 0x00000000201F15F8>,
        <matplotlib.axes._subplots.AxesSubplot object at 0x0000000019220630>],
       [<matplotlib.axes._subplots.AxesSubplot object at 0x00000000201E4D68>,
        <matplotlib.axes._subplots.AxesSubplot object at 0x0000000019207518>,
        <matplotlib.axes._subplots.AxesSubplot object at 0x000000001C8FEBA8>]],
      dtype=object)
      
type(axes) # numpy.ndarray
axes.shape # 3x3
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
subplot(nrows,ncols,plot_number)
```
```
import numpy as np
import matplotlib.pyplot as plt


x1 = np.linspace(0.0, 5.0)
x2 = np.linspace(0.0, 2.0)

y1 = np.cos(2 * np.pi * x1) * np.exp(-x1)
y2 = np.cos(2 * np.pi * x2)

plt.subplot(2, 1, 1)
plt.plot(x1, y1, 'o-')
plt.title('A tale of 2 subplots')
plt.ylabel('Damped oscillation')

plt.subplot(2, 1, 2)
plt.plot(x2, y2, '.-')
plt.xlabel('time (s)')
plt.ylabel('Undamped')

plt.show()

```
## matplotlib.pyplot.subplot2grid
```
subplot2grid(shape,loc,rowspan=1, colspan=1, **kwargs)
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



# Set The Color Of A Matplotlib Plot
## [Colormapas in Matplotlib](https://matplotlib.org/tutorials/colors/colormaps.html)


## Show matplotlib colormaps
```
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

## According to a single value to decide the colors
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


















