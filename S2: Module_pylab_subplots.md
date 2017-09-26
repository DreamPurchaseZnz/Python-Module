# subplots
Create a figure and a set of subplots
This utility wrapper makes it convenient to create common layouts of subplots
```
matplotlib.pyplot.subplots(nrows=1, ncols=1, sharex=False, sharey=False, 
squeeze=True, subplot_kw=None, gridspec_kw=None, **fig_kw)
```
### Parameters:
```
nrows, ncols                                                                   --->  int, optional, default: 1
sharex, sharey                                                                 --->  bool or {‘none’, ‘all’, ‘row’, ‘col’}
squeeze 
subplot_kw
gridspec_kw
**fig_kw                                                                       ---> figure() call below

```
### Return:
```
fig
ax
```
### Usage
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


figure()
----------------------------------------------------------------------------------------------------------------------------
```
matplotlib.pyplot.figure(num=None, figsize=None, dpi=None, facecolor=None, 
edgecolor=None, frameon=True, FigureClass=<class 'matplotlib.figure.Figure'>, **kwargs)
```
### Parameters
```
num                                  ---> integer or string, optional, default: none :number attribute
figsize                              ---> tuple of integer,(weight,heigt) units:inches
dpi                                  ---> resolution of figure
facecolor                            ---> the background color
edgecolor                            ---> border color
```

### return 
```
figure                               ---> The Figure instance returned will also be passed to new_figure_manager in the backends
```































