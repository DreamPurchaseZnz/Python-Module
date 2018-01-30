[numpy.Random](https://docs.scipy.org/doc/numpy/reference/routines.random.html)
-----------------------------------------------------------------------------------------------------------

## Simple random data
```
rand(d0, d1, ..., dn)               Random values in a given shape.
randn(d0, d1, ..., dn)              Return a sample (or samples) from the “standard normal” distribution.
randint(low[, high, size, dtype])   Return random integers from low (inclusive) to high (exclusive).
random_integers(low[, high, size])  Random integers of type np.int between low and high, inclusive.
random_sample([size])               Return random floats in the half-open interval [0.0, 1.0).
random([size])                      Return random floats in the half-open interval [0.0, 1.0).
ranf([size])                        Return random floats in the half-open interval [0.0, 1.0).
sample([size])                      Return random floats in the half-open interval [0.0, 1.0).
choice(a[, size, replace, p])       Generates a random sample from a given 1-D array
bytes(length)                       Return random bytes.
```

## Permutations
```
shuffle(x)                          Modify a sequence in-place by shuffling its contents.
permutation(x)                      If x is a multi-dimensional array, it is only shuffled along its first index.
```
## Distributions
```
beta(a, b[, size])
binomial(n, p[, size])
chisquare(df[, size])
dirichlet(alpha[, size])
exponential([scale, size])
f(dfnum, dfden[, size])
gamma(shape[, scale, size])
geometric(p[, size])
gumbel([loc, scale, size])
hypergeometric(ngood, nbad, nsample[, size])
laplace([loc, scale, size])
logistic([loc, scale, size])
lognormal([mean, sigma, size])
logseries(p[, size])
multinomial(n, pvals[, size])
multivariate_normal(mean, cov[, size, ...)
negative_binomial(n, p[, size])
noncentral_chisquare(df, nonc[, size])
noncentral_f(dfnum, dfden, nonc[, size])
normal([loc, scale, size])
pareto(a[, size])
poisson([lam, size])
power(a[, size])
rayleigh([scale, size])
standard_cauchy([size])
standard_exponential([size])
standard_gamma(shape[, size])
standard_normal([size])
standard_t(df[, size])
triangular(left, mode, right[, size])
uniform([low, high, size])
vonmises(mu, kappa[, size])
wald(mean, scale[, size])
weibull(a[, size])
zipf(a[, size])
```
### [multivariable_normal](https://docs.scipy.org/doc/numpy/reference/generated/numpy.random.multivariate_normal.html)
Draw random samples from  a multivariable normal distribution.
such a distribution is specified by its mean and convariance matrix.
```
numpy.random.multivariate_normal(
mean,             ---> 1-D array-like (N,)
cov[,             ---> 2-D array-like (N, N)
size, 
check_valid,      ---> {'warning', 'raise', 'ignore'} if the covariance matrix is not positive semidefininate
tol
])
```
## Random generator
```
RandomState                       Container for the Mersenne Twister pseudo-random number generator.
seed([seed])                      Seed the generator.
get_state()                       Return a tuple representing the internal state of the generator.
set_state(state)                  Set the internal state of the generator from a tuple.
```

# Linear algebra
np.linalg
## Matrix and vector products
```
dot(a, b[, out])
linalg.multi_dot(arrays)
vdot(a, b)
inner(a, b)
outer(a, b[, out])
matmul(a, b[, out])
tensordot(a, b[, axes])
einsum(subscripts, *operands[, out, dtype, ...])
einsum_path(subscripts, *operands[, optimize])
linalg.matrix_power(M, n)
kron(a, b)
```
## Decompositions
```
linalg.cholesky(a)
linalg.qr(a[, mode])
linalg.svd(a[, full_matrices, compute_uv])
```
## Matrix eigenvalues
```
linalg.eig(a)
linalg.eigh(a[, UPLO])
linalg.eigvals(a)
linalg.eigvalsh(a[, UPLO])
```
## Norm and other numbers
```
linalg.norm(x[, ord, axis, keepdims])
linalg.cond(x[, p])
linalg.det(a)
linalg.matrix_rank(M[, tol, hermitian])
linalg.slogdet(a)
trace(a[, offset, axis1, axis2, dtype, out])
```
## Solving equations and inverting matrices
```
linalg.solve(a, b)
linalg.tensorsolve(a, b[, axes])
linalg.lstsq(a, b[, rcond])
linalg.inv(a)
linalg.pinv(a[, rcond])
linalg.tensorinv(a[, ind])
```


