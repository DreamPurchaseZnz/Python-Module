# OS.path
the most frequently method used in os.path module
```
os.path.dirname(path)                                 --->  Return the directory name
os.path.exists(path)                                  --->  Return True if path refers to an existing path
os.path.join(path, *paths)                            --->  Join one or more path components intelligently.Note that since there is a                                                                 current directory for each drive, os.path.join("c:", "foo") represents a path                                                             relative to the current directory on drive C: (c:foo), not c:\foo.
os.path.split(path)                                   --->  Split the pathname path into a pair, (head, tail) where tail is the last                                                                 pathname component and head is everything leading up to that
os.path.splitdrive(path)                              --->  Split the pathname path into a pair (drive, tail) 
os.path.splitext(path)                                
```
