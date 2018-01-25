# Strings
## Print
In principle, every computer program has to communicate with the environment or the "outside world".
To this purpose nearly every programming language has special I/O functionalities, i.e. input/output

The arguments of the print function are the following ones:
```
print(
value1, ...,                --> an arbitrary number of values
sep=' ',                    --> output is separated by blanks
end='\n',                   --> the values' end  
file=sys.stdout,            --> pass to the interpreter
flush=False)
```
The print function can print an arbitrary number of values ("value1, value2, ..."), which are separated by commas. These values are separated by blanks. 
```
print('a','b','c')            # a b c
print("a", "b", sep='')       # ab
print("a", "b", sep=':->')    # a:->b
print(192, 168, 6006,sep='.') # 192.168.6006
```
A print call is ended by a newline, as we can see in the following usage:
```
[print(i) for i in range(3)]
0
1
2
# [None, None, None]
```
To change the behavior, we can change the keyword *end*, this string will be used for ending the output of the values of  print call
```
for i in range(3):
    print(i, end=':->')   
0:->1:->2:->
```
The output of the print function is send to the standard output stream (sys.stdout) by default. By redefining the keyword parameter "file" we can send the output into a different stream e.g. sys.stderr or a file:
```
fh =  open('print.txt','w')
print('42 is the answer, but what is the question?' , file=fh)
fh.close()
```
you can see a *print.txt* file, the content is:
```
42 is the answer, but what is the question?
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


