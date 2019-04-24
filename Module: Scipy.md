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

## DCT
Return the Discrete Cosine Transform of arbitrary type sequence x
```
scipy.fftpack.dct(
x, 
type=2, 
n=None, 
axis=-1, 
norm=None, 
overwrite_x=False
)
```


## [signal processing](https://docs.scipy.org/doc/scipy/reference/signal.html)
```
Convolution
B-splines
Filtering
Matlab-style IIR filter design
Continuous-Time Linear Systems
Discrete-Time Linear Systems
LTI Representations
Waveforms
Window functions
Wavelets
Peak finding
Spectral Analysis
```

```
lfiter
```




## File IO
### matlab file
```
loadmat(file_name[, mdict, appendmat])                # Load MATLAB file.
savemat(file_name, mdict[, appendmat, …])             # Save a dictionary of names and arrays into a MATLAB-style .mat file.
whosmat(file_name[, appendmat])                       # List variables inside a MATLAB file.
```
### Wav sound files 
```
scipy.io.wavfile

    read                  Open a WAV file
    write                 Write a numpy array as a WAV file
```




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

