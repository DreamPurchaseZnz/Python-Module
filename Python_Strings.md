# Strings
## Print
In principle, every computer program has to communicate with the environment or the "outside world".
To this purpose nearly every programming language has special I/O functionalities, i.e. input/output
The arguments of the print function are the following ones:
```
print(value1, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
```

## [Multi strings in Python](https://www.smallsurething.com/multi-line-strings-in-python/)
At some points We will want to define a multi-line string and find that the obvious solution just don't feel clean.
There are three method:

### CONCATENATION
```
template = "This is the first line.\n" 
           "This is the second line.\n" 
           "This is the third line."
           
print(template)
```


