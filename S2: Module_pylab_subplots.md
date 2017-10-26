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





























