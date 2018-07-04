## Imshow
```
X : array_like, 
shape (n, m) 
or (n, m, 3) 
or (n, m, 4)
Display the image in X to current axes. 
X may be an array or a PIL image. 

If X is an array, it can have the following shapes and types:

MxN – values to be mapped (float or int)
MxNx3 – RGB (float or uint8)
MxNx4 – RGBA (float or uint8)

MxN arrays are mapped to colors based on the norm (mapping scalar to scalar) 
and the cmap (mapping the normed scalar to a color).

Elements of RGB and RGBA arrays represent pixels of an MxN image.
All values should be in the 

range [0 .. 1] for 
floats or [0 .. 255] for integers. 

Out-of-range values will be clipped to these bounds.
```
```
matplotlib.pyplot.imshow(
X, 
cmap=None, 
norm=None, 
aspect=None, 
interpolation=None, 
alpha=None, 
vmin=None, 
vmax=None, 
origin=None, 
extent=None, 
shape=None, 
filternorm=1, 
filterrad=4.0, 
imlim=None, 
resample=None, 
url=None, 
hold=None, data=None, **kwargs)
```
