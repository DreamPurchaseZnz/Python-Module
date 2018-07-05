# [glob](https://docs.python.org/3/library/glob.html)
Unix style pathname pattern expansion

## Functionality
find all the pathnames matching a specified pattern

```
glob.glob(
pathname,                    ---> pattern
*,
recursive=False)

Return
--------------------
a possibly-empty list of path names that match pathname
```

```
glob.escape(pathname)
```

## Example
```
glog.glob("./result/*.py")

```
