# Scipy

- Basic functions
- Special functions (scipy.special)
- Integration (scipy.integrate)
- Optimization (scipy.optimize)
- Interpolation (scipy.interpolate)
- Fourier Transforms (scipy.fftpack)
- Signal Processing (scipy.signal)
- Linear Algebra (scipy.linalg)
- Sparse Eigenvalue Problems with ARPACK
- Compressed Sparse Graph Routines (scipy.sparse.csgraph)
- Spatial data structures and algorithms (scipy.spatial)
- Statistics (scipy.stats)
- Multidimensional image processing (scipy.ndimage)
- File IO (scipy.io)

## Statistics
This module contains a large number of probability distributions as well as a growing library of statistical functions
- Continuous distributions
- Multivariate distributions
- Discrete distributions
- Special functions
- Circular statistical functions
- Contingency table functions
- Plot tests
- Masked statistics functions
- Univariate and multivariate kernel density estimation

scipy.stats.kde
```
class scipy.stats.gaussian_kde(
dataset,                  ---> datapoints to estimate from. 2-D array with shape[dim, data],i.e.,pxn
bw_method=None            ---> optional, str, scalar("kde.factor") or callable("scott", "silverman")
)
```

