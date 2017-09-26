# Axes class
the axes contains the most of the figure elements:Axis, Tick, Line2D, Text, Polygon, etc and sets the coordinate system
```
class matplotlib.axes.Axes(fig, rect, facecolor=None, frameon=True, sharex=None, sharey=None, label='', xscale=None, yscale=None, axisbg=None, **kwargs)
```
### Plotting
```
Axes.plot                              ---> plot lines and/or markers 
Axes.errorbar
Axes.scatter                           ---> Make a scatter plot x Vs y
Axes.plot_date                         ---> data contains dates
Axes.step
Axes.loglog
Axes.semilogx
Axes.semilogy
Axes.fill_between                      ---> Make filled polygons between two curves
Axes.fill_betweenx
Axes.bar
Axes.barh                              ---> Plot a horizontal curves
Axes.stem
Axes.eventplot
Axes.pie
Axes.stackplot                         ---> Plot stack plot
Axes.broken_barh
Axes.vlines                            ---> Plot vertical lines
Axes.hlines                            ---> plot horizontal lines
Axes.fill                              ---> plot polygons
```
### Spans
```
Axes.axhline                           ---> like hlines
Axes.axhspan
Axes.axvline
Axes.axvspan
```
### Statistics
```

Axes.boxplot                          ---> make a box and whisger plot
Axes.violinplot                       ---> make a violin plot
Axes.violin
Axes.bxp
```
### Binned
```

Axes.hexbin
Axes.hist
Axes.hist2d                           ---> 2D demensional data
```
### Contours
```
Axes.clabel 
Axes.contour
Axes.contourf
```
### Array
```
Axes.imshow                          ---> Display an image on axes                  
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
Axes.annotate                    ---> annotate the point x,y with text s
Axes.text                       
Axes.table	
Axes.arrow	

```
### Fields
```

Axes.barbs
Axes.quiver
Axes.quiverkey
Axes.streamplot
```
## Clearing
```
Axes.cla                        ---> clear the current axes.
Axes.clear	                    ---> clear the axes
```
## Appearance
```

Axes.axis
Axes.set_axis_off               ---> Turn axis off
Axes.set_axis_on                ---> Turn axis on
Axes.set_frame_on
Axes.get_frame_on 
Axes.set_axisbelow              ---> Set whether the axis ticks and gridlines 
Axes.get_axisbelow
Axes.grid                       ---> Turn the axes grids on or off
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
Axes.invert_xaxis                         ---> Invert the x-axis
Axes.invert_yaxis                         ---> Invert the y-axis
Axes.xaxis_inverted
Axes.yaxis_inverted
Axes.set_xlim                             ---> Set the data limits for the x-axis
Axes.set_ylim                             ---> Set the data limits for the y-axis
Axes.get_ylim
Axes.get_xlim
Axes.update_datalim
Axes.update_datalim_bounds
Axes.update_datalim_numerix	
Axes.set_ybound                          ---> Set the lower and upper numerical bounds of the y-axis.
Axes.set_xbound                          ---> Set the lower and upper numerical bounds of the x-axis.
Axes.get_ybound
Axes.get_xbound

```
### Axis Labels, title, and legend
```
Axes.get_xlabel
Axes.get_ylabel
Axes.set_xlabel                          ---> Set the label for the xaxis.
Axes.set_ylabel                          ---> Set the label for the yaxis
Axes.set_title                           ---> Set a title for the axes.
Axes.get_title
Axes.legend                              ---> Places a legend on the axes.
Axes.get_legend
Axes.get_legend_handles_labels
```
### Axis scales
```
Axes.set_xscale                          ---> Set the x-axis scale e.g log etc
Axes.get_xscale                          ---> Return the xaxis scale string: linear, log, logit, symlog
Axes.get_yscale
Axes.set_yscale
```
### Autoscaling and margins
```

Axes.use_sticky_edges	When autoscaling, whether to obey all Artist.sticky_edges.
Axes.margins	Set or retrieve autoscaling margins.
Axes.set_xmargin	Set padding of X data limits prior to autoscaling.
Axes.set_ymargin	Set padding of Y data limits prior to autoscaling.
Axes.relim	Recompute the data limits based on current artists.
Axes.autoscale	Autoscale the axis view to the data (toggle).
Axes.autoscale_view	Autoscale the view limits using the data limits.
Axes.get_autoscale_on	Get whether autoscaling is applied for both axes on plot commands
Axes.set_autoscale_on	Set whether autoscaling is applied on plot commands
Axes.get_autoscalex_on	Get whether autoscaling for the x-axis is applied on plot commands
Axes.set_autoscalex_on	Set whether autoscaling for the x-axis is applied on plot commands
Axes.get_autoscaley_on	Get whether autoscaling for the y-axis is applied on plot commands
Axes.set_autoscaley_on	Set whether autoscaling for the y-axis is applied on plot commands

```














