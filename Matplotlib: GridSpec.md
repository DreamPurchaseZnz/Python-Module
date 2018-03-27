# [GridSpec](https://matplotlib.org/users/gridspec.html)
[constrainedlayout_guide](https://matplotlib.org/tutorials/intermediate/constrainedlayout_guide.html?highlight=constrained%20layout%20guide)

[tight_layout_guide](https://matplotlib.org/users/tight_layout_guide.html)

```
import matplotlib.pyplot as plt
import matplotlib.gridspec as gridspec
# ax = plt.subplot2grid((2, 2), (0, 0))
# ax2 = plt.subplot2grid((3, 3), (1, 0), colspan=2)
# ax3 = plt.subplot2grid((3, 3), (1, 2), rowspan=2)
```
## Basic Example of using subplot2grid
```
ax1 = plt.subplot2grid((2, 6), (0, 0), colspan=2)
ax2 = plt.subplot2grid((2, 6), (0, 2), colspan=2)
ax3 = plt.subplot2grid((2, 6), (0, 4), colspan=2)
ax4 = plt.subplot2grid((2, 6), (1, 1), colspan=2)
ax5 = plt.subplot2grid((2, 6), (1, 3), colspan=2)
```

## GridSpec and SubplotSpec
```
gs = gridspec.GridSpec(2, 2)
ax = plt.subplot(gs[0, 0])

gs = gridspec.GridSpec(3, 3)
ax1 = plt.subplot(gs[0, :])
ax2 = plt.subplot(gs[1, :-1])
ax3 = plt.subplot(gs[1:, -1])
ax4 = plt.subplot(gs[-1, 0])
ax5 = plt.subplot(gs[-1, -2])
```
### our case
The range is [a,b), where the b is not in the group and a=b+n
```
gs = gridspec.GridSpec(2, 6)
ax1 = plt.subplot(gs[0, 0:2])
ax2 = plt.subplot(gs[0, 2:4])
ax3 = plt.subplot(gs[0, 4:6])
ax4 = plt.subplot(gs[1, 1:3])
ax5 = plt.subplot(gs[1, 3:5])
```

## Adjust GridSpec layout
When a GridSpec is explicitly used, you can adjust the layout parameters
of subplots that are created from the GridSpec.
```
gs1 = gridspec.GridSpec(3, 3)
gs1.update(left=0.05, right=0.48, wspace=0.05)
ax1 = plt.subplot(gs1[:-1, :])
ax2 = plt.subplot(gs1[-1, :-1])
ax3 = plt.subplot(gs1[-1, -1])

gs2 = gridspec.GridSpec(3, 3)
gs2.update(left=0.55, right=0.98, hspace=0.05)
ax4 = plt.subplot(gs2[:, :-1])
ax5 = plt.subplot(gs2[:-1, -1])
ax6 = plt.subplot(gs2[-1, -1])
Here :
```
# left  = 0.125  # the left side of the subplots of the figure
# right = 0.9    # the right side of the subplots of the figure
# bottom = 0.1   # the bottom of the subplots of the figure
# top = 0.9      # the top of the subplots of the figure
# wspace = 0.2   # the amount of width reserved for blank space between subplots,
#                # expressed as a fraction of the average axis width
# hspace = 0.2   # the amount of height reserved for white space between subplots,
#                # expressed as a fraction of the average axis height
```
### in our case
```
gs = gridspec.GridSpec(2, 6)
gs.update(wspace=1, hspace=0.4)
ax1 = plt.subplot(gs[0, 0:2])
ax2 = plt.subplot(gs[0, 2:4])
ax3 = plt.subplot(gs[0, 4:6])
ax4 = plt.subplot(gs[1, 1:3])
ax5 = plt.subplot(gs[1, 3:5])
```
## GridSpec using SubplotSpec
You can create GridSpec from the SubplotSpec, in which case
its layout parameters are set to that of the location of the given SubplotSpec
```
gs0 = gridspec.GridSpec(1, 2)

gs00 = gridspec.GridSpecFromSubplotSpec(3, 3, subplot_spec=gs0[0])
gs01 = gridspec.GridSpecFromSubplotSpec(3, 3, subplot_spec=gs0[1])
```

## GridSpec with Varying Cell Sizes
By default, GridSpec creates cells of equal sizes. You can adjust relative heights and widths of rows and columns.
Note that absolute values are meaningless, only their relative ratios matter.
```
gs = gridspec.GridSpec(2, 2,
                       width_ratios=[1, 2],
                       height_ratios=[4, 1]
                       )
```




ax1 = plt.subplot(gs[0])
ax2 = plt.subplot(gs[1])
ax3 = plt.subplot(gs[2])
ax4 = plt.subplot(gs[3])
