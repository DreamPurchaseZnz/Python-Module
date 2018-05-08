# [Matplotlib.patches](https://matplotlib.org/api/patches_api.html)

## Class
```
Arc(xy, width, height[, angle, theta1, theta2])               An elliptical arc.
Arrow(x, y, dx, dy[, width])                                  An arrow patch.
ArrowStyle                                                    ArrowStyle is a container class which defines several
BoxStyle                                                      BoxStyle is a container class which defines several
Circle(xy[, radius])                                          A circle patch.
CirclePolygon(xy[, radius, resolution])                       A polygon-approximation of a circle patch.
ConnectionPatch(xyA, xyB, coordsA[, …])                       A ConnectionPatch class is to make connecting lines between 
                                                              two points (possibly in different axes).
ConnectionStyle                                               ConnectionStyle is a container class which defines
Ellipse(xy, width, height[, angle])                           A scale-free ellipse.
FancyArrow(x, y, dx, dy[, width, …])                          Like Arrow, but lets you set head width and head height independently.
FancyArrowPatch([posA, posB, path, …])                        A fancy arrow patch.
FancyBboxPatch(xy, width, height[, …])                        Draw a fancy box around a rectangle with 
                                                              lower left at xy*=(*x, y) with specified width and height.
Patch([edgecolor, facecolor, color, …])                       A patch is a 2D artist with a face color and an edge color.
PathPatch(path, **kwargs)                                     A general polycurve path patch.
Polygon(xy[, closed])                                         A general polygon patch.
Rectangle(xy, width, height[, angle])                         Draw a rectangle with lower left at xy = (x, y) with 
                                                              specified width, height and rotation angle.
RegularPolygon(xy, numVertices[, radius, …])                  A regular polygon patch.
Shadow(patch, ox, oy[, props])                                Create a shadow of the given patch offset by ox, oy.
Wedge(center, r, theta1, theta2[, width])                     Wedge shaped patch.
YAArrow(figure, xytip, xybase[, width, …])                    Yet another arrow class.

```
## Functions
```
bbox_artist(artist, renderer[, props, fill])                 
draw_bbox(bbox, renderer[, color, trans])
```

## [Arc](https://matplotlib.org/1.5.1/api/patches_api.html)
```
class matplotlib.patches.Arc(
xy, 
width, 
height, 
angle=0.0, 
theta1=0.0, 
theta2=360.0, 
**kwargs)
```
