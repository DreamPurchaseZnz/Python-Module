# Matplotlib
## Make tick labels font size smaller
```
import matplotlib.pyplot as plt
# We prepare the plot  
fig = plt.figure(1)
# We define a fake subplot that is in fact only the plot.  
ax = fig.add_subplot(111)
# We change the fontsize of minor ticks label 
ax.tick_params(axis='both', which='major', labelsize=10)
ax.tick_params(axis='both', which='minor', labelsize=8)
```
The above solutions were close however they were not working out for me. I found my solution from this matplotlib page.
```
ax.xaxis.set_tick_params(labelsize=20)

```


## Plt.tight_layout()
plotting a dataset using matplotlib where I have an xlabel that is quite "tall" (it's a formula rendered in TeX that contains a fraction and is therefore has the height equivalent of a couple of lines of text).

In any case, the bottom of the formula is always cut off when I draw the figures. Changing figure size doesn't seem to help this, and I haven't been able to figure out how to shift the x-axis "up" to make room for the xlabel. Something like that would be a reasonable temporary solution, but what would be nice would be to have a way to make matplotlib recognize automatically that the label is cut off and resize accordingly.



## Starting a new figure
First method:
```
plt.figure(figsize=(10, 3.5))

plt.subplot(1, 2, 1)
plt.imshow(I, cmap='RdBu')
plt.colorbar()
```
```
import pylab as plt
import numpy as np
my_image1 = np.linspace(0, 10, 10000).reshape(100,100)
my_image2 = np.sqrt(my_image1.T) + 3
plt.subplot(1, 2, 1)
plt.imshow(my_image1, vmin=0, vmax=10, cmap='jet', aspect='auto')
plt.subplot(1, 2, 2)
plt.imshow(my_image2, vmin=0, vmax=10, cmap='jet', aspect='auto')
plt.colorbar()
```
Second method
```
from sklearn.datasets import load_digits
digits = load_digits(n_class=6)

fig, ax = plt.subplots(8, 8, figsize=(6, 6))
for i, axi in enumerate(ax.flat):
    axi.imshow(digits.images[i], cmap='binary')
    axi.set(xticks=[], yticks=[])
```
```

import matplotlib.pyplot as plt
import numpy as np

fig, axes = plt.subplots(nrows=2, ncols=3, figsize=(8.5, 5))

for ax in axes.flat:
    ax.set_axis_off()
    im = ax.imshow(np.random.random((16, 16)), cmap='viridis',
                   vmin=0, vmax=1)

fig.subplots_adjust(bottom=0.1, top=0.9, left=0.1, right=0.8,
                    wspace=0.02, hspace=0.02)

# add an axes, lower left corner in [0.83, 0.1] measured in figure coordinate with axes width 0.02 and height 0.8

cb_ax = fig.add_axes([0.83, 0.1, 0.02, 0.8]) # add_axes(rect, projection=None, polar=False, **kwargs)
                                             # add_axes(ax)
cbar = fig.colorbar(im, cax=cb_ax)

 set the colorbar ticks and tick labels
cbar.set_ticks(np.arange(0, 1.1, 0.5))
cbar.set_ticklabels(['low', 'medium', 'high'])

plt.show()
```
```
import matplotlib.pyplot as plt
import numpy as np

fig, axes = plt.subplots(nrows=2, ncols=3, figsize=(8.5, 5))

for ax in axes.flat:
    ax.set_axis_off()
    im = ax.imshow(np.random.random((16, 16)), cmap='viridis',
                   vmin=0, vmax=1)

# notice that here we use ax param of figure.colorbar method instead of

# the cax param as the above example

cbar = fig.colorbar(im, ax=axes.ravel().tolist(), shrink=0.95)

cbar.set_ticks(np.arange(0, 1.1, 0.5))
cbar.set_ticklabels(['low', 'medium', 'high'])

plt.show()
```
Third method:
```
fig = plt.figure(figsize=(9, 9))
ax = fig.add_subplot(121)
ax.imshow(lab_feat, cmap="jet")
ax2 = fig.add_subplot(122)
ax2.imshow(acou_feat, cmap="jet")
ax2.colorbar()
plt.show()
```



## savefig
```
savefig(fname, dpi=None, facecolor='w', edgecolor='w',
        orientation='portrait', papertype=None, format=None,
        transparent=False, bbox_inches=None, pad_inches=0.1,
        frameon=None, metadata=None)
```



# [Axes class](https://matplotlib.org/api/axes_api.html)


```
class matplotlib.axes.Axes(
fig, 
rect, 
facecolor=None,
frameon=True, 
sharex=None, 
sharey=None, 
label='', 
xscale=None, 
yscale=None, 
axisbg=None, 
**kwargs)
```
the axes contains the most of the figure elements and sets the coordinate system
- Axis
- Tick
- Line2D
- Text
- Polygon
- etc 
- Basic plot

## BASIC PLOT
### Plotting
```
Axes.plot                                                           ---> plot lines and/or markers 
Axes.errorbar
Axes.scatter                                                        ---> Make a scatter plot x Vs y
Axes.plot_date                                                      ---> data contains dates
Axes.step
Axes.loglog
Axes.semilogx
Axes.semilogy
Axes.fill_between                                                   ---> Make filled polygons between two curves
Axes.fill_betweenx
Axes.bar
Axes.barh                                                           ---> Plot a horizontal curves
Axes.stem
Axes.eventplot
Axes.pie
Axes.stackplot                                                      ---> Plot stack plot
Axes.broken_barh
Axes.vlines                                                         ---> Plot vertical lines
Axes.hlines                                                         ---> plot horizontal lines
Axes.fill                                                           ---> plot polygons
```
#### Plot
```
Axes.plot(
*args,
data=None, 
**kwargs
)
```
If x and/or y is 2-dimensional, 
then the corresponding columns will be plotted.

#### Scatter
```
Axes.scatter(
x,y,                               ---> array_like, shape(n,) 
s=None,                            ---> scalar or array_like, shape(n,),optional
                                        size in points^2
c=None,                            ---> color, sequence, or sequence of color, optional,default:'b'
                                        c can be a sigle color format string or a sequence of color specificaiton of length N
                                        or a sequence of N numbers to be mapped to colors using the cmap and norm. c can be a
                                        2-D array in which the rows are RGB or RGBA
marker=None,                       ---> 'Markerstyle'
cmap=None,                         ---> 'Colormap'
norm=None,                         ---> 'Normalize', can normalize data into the [0,1] interval; norm only used if c in an array of
                                         floats
vmin=None, vmax=None,              ---> vmin and vmax are used in conjunction with norm to normalize luminance data 
alpha=None,                        ---> scalar,optional, 0(transparent) and 1 (opaque)
linewidths=None,                   ---> scalar, or array_like
verts=None,           
edgecolors=None,                   ---> color or sequence of color, if 'face', the edge color will be the same as the face color. 
**kwargs)


```

### Spans
```
Axes.axhline                                                        ---> like hlines
Axes.axhspan
Axes.axvline
Axes.axvspan
```
### Statistics
```

Axes.boxplot                                                       ---> make a box and whisger plot
Axes.violinplot                                                    ---> make a violin plot
Axes.violin
Axes.bxp
```
### Binned
```

Axes.hexbin
Axes.hist
Axes.hist2d                                                        ---> 2D demensional data
```
#### hist
the return value is a tupe(n, bins, patches)
```
matplotlib.pyplot.hist(
x,                                           ---> array(n,) or sequence of (n,) arrays
bins=None,                                   ---> integer(bin number) or sequence(bin edges) or ‘auto’, optional
range=None,                                  ---> the range of bins, lower or higher outliers are ignored
density=None,                                ---> boolean, optional; the area under the histogram will sum to 1
weights=None,                                ---> (n, ) array_like or None, optional
cumulative=False,                            ---> boolean, optional;  computed where each bin gives the counts 
                                                  in that bin plus all bins for smaller values 
bottom=None,                                
histtype='bar',                              ---> {‘bar’, ‘barstacked’, ‘step’, ‘stepfilled’}, optional
align='mid',                                 ---> {‘left’, ‘mid’, ‘right’}, optional
orientation='vertical',                      ---> {‘horizontal’, ‘vertical’}, optional
rwidth=None, log=False,                      ---> scalar or None, optional; The relative width of the bars 
                                                  as a fraction of the bin width
color=None,                                  ---> color or array_like of colors or None, optional
label=None,                                  ---> string or None, optional
stacked=False,                               ---> boolean, optional;
                                                  If True, multiple data are stacked on top of each other 
                                                  If False multiple data are aranged side by side 
                                                  if histtype is ‘bar’ or on top of each other if histtype is ‘step’
normed=None,             
hold=None, 
data=None, 
```
return
```
n                                           ---> array or list of arrays
bins                                        ---> array
patches                                     ---> list or list of lists
```
Example:
```
import numpy as np
import matplotlib.pyplot as plt

# Fixing random state for reproducibility
np.random.seed(19680801)

mu, sigma = 100, 15
x = mu + sigma * np.random.randn(10000)

# the histogram of the data
n, bins, patches = plt.hist(x, 50, normed=1, facecolor='g', alpha=0.75)


plt.xlabel('Smarts')
plt.ylabel('Probability')
plt.title('Histogram of IQ')
plt.text(60, .025, r'$\mu=100,\ \sigma=15$')
plt.axis([40, 160, 0, 0.03])
plt.grid(True)
plt.show()
```


### Contours
```
Axes.clabel 
Axes.contour
Axes.contourf
```
### Array
```
Axes.imshow                                                       ---> Display an image on axes                  
Axes.matshow
Axes.pcolor
Axes.pcolorfast
Axes.pcolormesh
Axes.spy
```
```
Axes.imshow(
X,                             ---> array_like, shape(n, m) or (n, m, 3) or (n, m, 4)              
cmap=None,                     ---> colormap
norm=None, 
aspect=None, 
interpolation=None, 
alpha=None, 
vmin=None, vmax=None, origin=None, extent=None, shape=None,
filternorm=1, filterrad=4.0, imlim=None, resample=None,
url=None, *, data=None, **kwargs)

```

### Unstructured Triangles
```

Axes.tripcolor
Axes.triplot
Axes.tricontour
Axes.tricontourf
```

### Text and Annotations
```
Axes.annotate                                                    ---> annotate the point x,y with text s
Axes.text                       
Axes.table	
Axes.arrow	
```
Add text to the axes
```
matplotlib.pyplot.text(
x, y,                   ---> scalars; data coordinates
s,                      ---> string; text
fontdict=None, 
withdash=False, 
**kwargs                ---> horizontalalignment; verticalalignment; etc 
)
```
### Fields
```

Axes.barbs
Axes.quiver
Axes.quiverkey
Axes.streamplot
```


## SET DETAILS
### Clearing
```
Axes.cla                                                       ---> clear the current axes.
Axes.clear	                                                   ---> clear the axes
```
### Appearance
```

Axes.axis
Axes.set_axis_off                                              ---> Turn axis off
Axes.set_axis_on                                               ---> Turn axis on
Axes.set_frame_on
Axes.get_frame_on 
Axes.set_axisbelow                                             ---> Set whether the axis ticks and gridlines 
Axes.get_axisbelow
Axes.grid                                                      ---> Turn the axes grids on or off
Axes.get_axis_bgcolor	
Axes.get_facecolor	
Axes.get_fc	
Axes.set_facecolor	
Axes.set_fc	
Axes.set_axis_bgcolor	
```
```
Axes.set_axis_off()                ---> turn off the axis

```

### Axis / limits
```
Axes.get_yaxis
Axes.get_xaxis
```
### Axis Limits and direction
```
Axes.invert_xaxis                                             ---> Invert the x-axis
Axes.invert_yaxis                                             ---> Invert the y-axis
Axes.xaxis_inverted
Axes.yaxis_inverted
Axes.set_xlim                                                 ---> Set the data limits for the x-axis
Axes.set_ylim                                                 ---> Set the data limits for the y-axis
Axes.get_ylim
Axes.get_xlim
Axes.update_datalim
Axes.update_datalim_bounds
Axes.update_datalim_numerix	
Axes.set_ybound                                               ---> Set the lower and upper numerical bounds of the y-axis.
Axes.set_xbound                                               ---> Set the lower and upper numerical bounds of the x-axis.
Axes.get_ybound
Axes.get_xbound

```
### Axis Labels, title, and legend
```
Axes.get_xlabel
Axes.get_ylabel
Axes.set_xlabel                                               ---> Set the label for the xaxis.
Axes.set_ylabel                                               ---> Set the label for the yaxis
Axes.set_title                                                ---> Set a title for the axes.
Axes.get_title
Axes.legend                                                   ---> Places a legend on the axes.
Axes.get_legend
Axes.get_legend_handles_labels
```
Set a title for the axes
```
Axes.set_title(
label,                            ---> str Text to use for title
fontdict=None,                    ---> A dictionary controlling the appearance of the title text
loc='center',                     ---> {'center', 'left','right'}
**kwargs)
```
*The bbox_to_anchor method of Legend*:[From stackoverflow](https://stackoverflow.com/questions/39803385/what-does-a-4-element-tuple-argument-for-bbox-to-anchor-mean-in-matplotlib)
```
loc:
bbox_to_anchor:
ncol:
prop:
mode: {extend,none}
```
```
import matplotlib.pyplot as plt
import numpy as np
import matplotlib.patches as patches

locs = ['upper right', 'lower left', 'center left', 'lower center', 'center',
        'right']

x0, y0, width, height = 0.5, 0.5, 0.1, 0.4

x = np.arange(0.1, 4, 0.1)
y = 1.0/x

fig = plt.figure(figsize=(10, 10))

idx = 1
for i in range(0, 2):
    for j in range(0, 3):
        ax = fig.add_subplot(3, 2, idx)
        ax.plot(x, y, label=r'$\frac{1}{x}$')
        ax.legend(loc=locs[idx-1], bbox_to_anchor=(x0, y0, width, height),
            edgecolor='g', fontsize='large', framealpha=0.5,
            borderaxespad=0)
        ax.add_patch(
            patches.Rectangle((x0, y0), width, height, color='r',
                            fill=False, transform=ax.transAxes)
        )
        ax.text(0.6, 0.2, s="loc = '{}'".format(locs[idx-1]),
        transform=ax.transAxes)
        idx += 1

plt.show()

```
```

import matplotlib.pyplot as plt
import numpy as np
import matplotlib.patches as patches

locs = ['upper right', 'lower left', 'center left', 'lower center', 'center',
        'right']

x0, y0, width, height = 0.5, 0.5, 0, 0

x = np.arange(0.1, 4, 0.1)
y = 1.0/x

fig = plt.figure(figsize=(10, 10))

idx = 1
for i in range(0, 2):
    for j in range(0, 3):
        ax = fig.add_subplot(3, 2, idx)
        ax.plot(x, y, label=r'$\frac{1}{x}$')
        ax.legend(loc=locs[idx-1], bbox_to_anchor=(x0, y0, width, height),
            edgecolor='g', fontsize='large', framealpha=0.5,
            borderaxespad=0)
        ax.add_patch(
            patches.Rectangle((x0, y0), width, height, color='r',
                            fill=False, transform=ax.transAxes)
        )
        ax.text(0.6, 0.2, s="loc = '{}'".format(locs[idx-1]),
        transform=ax.transAxes)
        ax.plot(x0, y0, 'r.', markersize=8, transform=ax.transAxes)
        idx += 1

plt.show()
```
Also can be seen in [another stackoverflow](https://stackoverflow.com/questions/4700614/how-to-put-the-legend-out-of-the-plot)
### Axis scales
```
Axes.set_xscale                                               ---> Set the x-axis scale e.g log etc
Axes.get_xscale                                               ---> Return the xaxis scale string: linear, log, logit, symlog
Axes.get_yscale
Axes.set_yscale
```
### Autoscaling and margins
```
Axes.use_sticky_edges
Axes.margins
Axes.set_xmargin
Axes.set_ymargin
Axes.relim.
Axes.autoscale
Axes.autoscale_view
Axes.get_autoscale_on                                        ---> Set whether autoscaling for the x-axis is applied on plot commands
Axes.set_autoscale_on 
Axes.get_autoscalex_on
Axes.set_autoscalex_on
Axes.get_autoscaley_on
Axes.set_autoscaley_on
```



### Ticks and tick labels
```

Axes.xaxis_date
Axes.yaxis_date
Axes.get_xmajorticklabels
Axes.get_xminorticklabels
Axes.get_xticklabels
Axes.get_xticklines
Axes.get_xticks
Axes.get_ymajorticklabels
Axes.get_yminorticklabels
Axes.get_yticklabels
Axes.get_yticklines
Axes.get_yticks
Axes.minorticks_off
Axes.minorticks_on
Axes.set_xticklabels                                      ---> Set the xtick labels with list of strings labels
Axes.set_xticks                                           ---> Set the x ticks with list of ticks
Axes.set_yticklabels
Axes.set_yticks
Axes.get_xgridlines
Axes.get_ygridlines
Axes.ticklabel_format
Axes.tick_params                                          ---> Change the appearance of ticks and tick labels
Axes.locator_params
```
### Adding Artists
```
Axes.add_artist
Axes.add_collection
Axes.add_container
Axes.add_image                                            ---> Add a AxesImage to the axes.
Axes.add_line
Axes.add_patch
Axes.add_table
```
### Twinning
```  
Axes.twinx                                                ---> Create a twin Axes sharing the xaxis
Axes.twiny                                                ---> Create a twin Axes sharing the yaxis
Axes.get_shared_x_axes
Axes.get_shared_y_axes

```
### Axes Position
```

Axes.get_anchor	
Axes.set_anchor                                           ---> Set anchor. 'C' :center
Axes.get_axes_locator
Axes.set_axes_locator
Axes.reset_position
Axes.get_position
Axes.set_position                                         ---> Set the axes position: pos = [left, bottom, width, height]

```
```
ax.get_anchor()      # 'C'
ax.set_anchor("SW")
```



-------------------------------------------------------------------------------------------------------------------
                                                 ADVANCED METHOD ABOUT ARTIST
-------------------------------------------------------------------------------------------------------------------
## Interactive
```
Axes.can_pan
Axes.can_zoom
Axes.get_navigate
Axes.set_navigate
Axes.get_navigate_mode
Axes.set_navigate_mode
Axes.start_pan
Axes.drag_pan
Axes.end_pan
Axes.format_coord
Axes.format_cursor_data
Axes.format_xdata
Axes.format_ydata
Axes.hitlist
Axes.mouseover	
Axes.in_axes
Axes.pick
Axes.pickable
Axes.get_picker
Axes.set_picker
Axes.set_contains
Axes.get_contains
Axes.contains
Axes.contains_point
Axes.get_cursor_data
Axes.get_cursor_props
Axes.set_cursor_props
```
## Children
> Pass

## Drawing
> Pass

## Bulk property manipulation
```
Axes.set                   ---> A property batch setter. Pass kwargs to set properties
Axes.update
Axes.properties            ---> Return a dictionary mapping property name
Axes.update_from           ---> Copy properties from other to self
```
As the subsection title depitched, we can set a batch of properties.
```
ax.set(xlim=[-1, 1], ylim=[-1, 1], xscale='linear', title='Hi')
Out[28]: 
[(-1, 1), None, (-1, 1), <matplotlib.text.Text at 0x1af71908>]
```
```
ax.properties()
Out[29]: 
{'adjustable': 'box',
 'agg_filter': None,
 'alpha': None,
 'anchor': 'C',
 'animated': False,
....
```

## General Artist Properties
> Pass

## Artist Methods
> Pass

## Other











