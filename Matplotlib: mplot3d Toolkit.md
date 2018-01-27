# Mplot3d
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


