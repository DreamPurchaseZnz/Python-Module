# module: os
>The Python Standard Library: File and Directory Access and Generic Operating System Services


---------------------------------------------------------------------------------------------------------
Miscellaneous operating system interfaces

## Process Parameters             
These functions and data items provide information and operate on the current process and user
```
os.getcwd()
os.getpid()                     --->  Return the current process id.
```

## File Object Creation
These functions create new file objects
```
os.fdopen
os.popen
os.tmpfile
```
## File Descriptor Operations
These functions operate on I/O streams referenced using file descriptors.
```
os.close
os.closerange
os.open
os.write
```
## Files and Directories
```
os.listdir                                          --->  Return a list containing the names of the entries in the directory 

os.mkdir                                            --->  Create a directory 
os.makedirs
os.chdir                                            --->  Change the working directory to the dirname
os.remove                                           --->  Remove (delete) the file
os.rmdir                                            --->  Remove a directory
os.removedirs
os.rename
os.renames
os.symlink                                          --->  Create a symbolic link pointing to source named link_name
os.stat

```

## Process Management
These functions may be used to create and manage processes
```
os.abort
os.kill
os.killpg
os.system
os.wait
```
## Miscellaneous System Information
```
os.confstr
os.sysconf                                        --->  Return integer-valued system configuration values
```
## Miscellaneous Functions
```
os.urandom
```

## Class: OS.path
the most frequently method used in os.path module
```
os.path.dirname(path)                                 --->  Return the directory name
os.path.exists(path)                                  --->  Return True if path refers to an existing path

os.path.abspath                                       --->  Return a normalized absolutized version of the pathname path,this is 
                                                            equivalent to normpath(join(os.getcwd(), path)).
os.path.normpath                                      --->  Normalize a pathname by collapsing redundant separators and up-level 
                                                            references so that A//B, A/B/, A/./B and A/foo/../B all become A/B
x`

os.path.join(path, *paths)                            --->  Join one or more path components intelligently
os.path.split(path)                                   --->  Split the pathname path into a pair, (head, tail) 
os.path.splitdrive(path)                              --->  Split the pathname path into a pair (drive, tail) 
os.path.splitext(path)                                
```
# Module : shutil 
—High-level file operations

functions provided in shutil support file copying and removal as following:
```
shutil.copyfile         
shutil.copytree                                      --->  Recursively copy an entire directory tree rooted at src
shutil.rmtree                                        --->  Delete an entire directory tree; path must point to a directory
shutil.move                                          
```
Archiving operations to create and read compressed and archived files relying on zipfile and tarfile modules
```
shutil.make_archive
shutil.get_archive_formats
shutil.register_archive_format
shutil.unregister_archive_format
```

# Module : sys 
—System-specific parameters and functions

