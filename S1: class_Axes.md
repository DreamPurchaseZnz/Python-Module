# Axes class
the axes contains the most of the figure elements:Axis, Tick, Line2D, Text, Polygon, etc and sets the coordinate system
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

----------------------------------------------------------------------------------------------------------------------------
                                                   BASIC PLOT
----------------------------------------------------------------------------------------------------------------------------

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

-----------------------------------------------------------------------------------------------------------------------------
                                                  SET DETAILS
-----------------------------------------------------------------------------------------------------------------------------
## Clearing
```
Axes.cla                                                       ---> clear the current axes.
Axes.clear	                                                   ---> clear the axes
```
## Appearance
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
## Axis / limits
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

-------------------------------------------------------------------------------------------------------------------
                                                  USUAL METHOD ABOUT ARTIST
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
> Pass

## General Artist Properties
> Pass

## Artist Methods
> Pass

## Other











