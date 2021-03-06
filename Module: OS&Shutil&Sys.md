# module: os
The Python Standard Library: File and Directory Access and Generic Operating System Services
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
os.listdir                                          --->  Return a list containing the names of 
                                                          the entries in the directory 
os.mkdir                                            --->  Create a directory 
os.makedirs
os.chdir                                            --->  Change the working directory to the dirname
os.remove                                           --->  Remove (delete) the file
os.rmdir                                            --->  Remove a directory
os.removedirs
os.rename
os.renames
os.symlink                                          --->  Create a symbolic link 
                                                          pointing to source named link_name
os.stat
```
*os.remove()* will remove a file.

*os.rmdir()* will remove an empty directory.

*shutil.rmtree()* will delete a directory and all its contents.
```
os.listdir(os.getcwd()) # ['.idea', 'block_provider', 'logs', 'Runet.py', 'RunRunet.py']

dirname = "c:\\"
[f for f in os.listdir(dirname)
    if os.path.isfile(os.path.join(dirname, f))]
Out[58]: 
['Aspen Engineering V8.4.log',
 'bootmgr',
 'BOOTNXT',
 'hiberfil.sys',
```
There is a more complex example, used for search the specific extension file.
```
def listDirectory(directory, fileExtList):                                        
    "get list of file info objects for files of particular extensions" 
    fileList = [os.path.normcase(f)
                for f in os.listdir(directory)]           
    fileList = [os.path.join(directory, f) 
               for f in fileList
                if os.path.splitext(f)[1] in fileExtList] 
    print(fileList)
    
listDirectory(os.getcwd(), ['.py'])
['C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\RU-Net\\runet.py', 
'C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\RU-Net\\runrunet.py']
```
of course, there is a package. So there will be more convenient to search what you want with pathon rather than the windows search function.
```
import glob
glob.glob(os.path.join(os.getcwd(),'*.py'))
Out[85]: 
['C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\RU-Net\\Runet.py',
 'C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\RU-Net\\RunRunet.py']
glob.glob('C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\*\\*.py')
Out[86]: 
['C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\data_providers\\base_provider.py',
 'C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\data_providers\\spectra.py',
 'C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\data_providers\\utils.py',
 'C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\data_providers\\__init__.py',
 'C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\RU-Net\\Runet.py',
 'C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\RU-Net\\RunRunet.py']
 
glob.glob('C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\*\\s*.py')
Out[87]: 
['C:\\Users\\CYD\\Desktop\\DenseNet_advanced\\data_providers\\spectra.py']
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

## [Class: OS.path](https://docs.python.org/3/library/os.path.html)
Common pathname manipulations
```
os.path.dirname(path)                                 --->  Return the directory name
os.path.exists(path)                                  --->  Return True if path refers to an existing path

os.path.abspath                                       --->  Normpath(join(os.getcwd(), path)).
os.path.normpath                                      --->  Normalize a pathname by collapsing 
                                                            redundant separators and up-level 
                                                            references

os.path.join(path, *paths)                            --->  Join one or more path 
                                                            components intelligently
os.path.split(path)                                   --->  Split the pathname path 
                                                            into a pair, (head, tail) 
os.path.splitdrive(path)                              --->  Split the pathname path 
                                                            into a pair (drive, tail) 
os.path.splitext(path)                                
os.path.isfile
os.path.isdir
os.path.islink
```
```
os.path.normpath('./z/n/z/./d')   # 'z\\n\\z\\d'
os.path.normpath('./z/n/z/.//d')  # 'z\\n\\z\\d'

os.path.join('./z/n', '/z')       # '/z'          ---> start with a slash, python consider 
                                                       the following part 
                                                       as an absolute path(for Unix like).
                                                       every thing before them is discarded
os.path.join('./z/n', '//z')      # '//z'         ---> Windows like \\[server name]\
os.path.join('./z/n', 'c:')       # 'c:'          ---> drive 
os.path.join('./z/n', 'c:','foo') # 'c:foo'
```
```
os.path.join("c:\\music\\ap\\", "mahadeva.mp3")  # 'c:\\music\\ap\\mahadeva.mp3'
os.path.join("c:\\music\\ap", "mahadeva.mp3")    # 'c:\\music\\ap\\mahadeva.mp3'
os.path.expanduser("~")                          # 'C:\\Users\\CYD'
os.path.join(os.path.expanduser("~"), "Python")  # 'C:\\Users\\CYD\\Python'
```
```
os.path.split("c:\\music\\ap\\mahadeva.mp3")     # ('c:\\music\\ap', 'mahadeva.mp3')
(filepath, filename) = os.path.split("c:\\music\\ap\\mahadeva.mp3") 
(shortname, extension) = os.path.splitext(filename) 
shortname  # 'mahadeva'
extension  # '.mp3'
```
# Module : [shutil](https://docs.python.org/2/library/shutil.html)
The shutil module offers a number of high-level operations on files and collections of files.
In particular, functions are provided which support file copying and removal.
For operations on individual files, see also the os module.

functions provided in shutil support file copying and removal as following:
```
shutil.copyfile         
shutil.copytree                                      --->  Recursively copy an entire 
                                                           directory tree rooted at src
shutil.rmtree                                        --->  Delete an entire directory tree; 
                                                           path must point to a directory
shutil.move
shutil.copy(src, dst)
```
Archiving operations to create and read compressed and archived files relying on zipfile and tarfile modules
```
shutil.make_archive
shutil.get_archive_formats
shutil.register_archive_format
shutil.unregister_archive_format
```
*shutil.copy* Copy the file src to the file or directory dst.If dst is a directory, a file with the same basename as src is created (or *overwritten*) in the directory specified. Permission bits are copied. src and dst are path names given as strings
```
shutil.copy(os.getcwd()+ '/base_options.py', './Test')
Out[66]: 
'./Test\\base_options.py'

```






# Module : sys 
This module provides access to some variables used or maintained by the interpreter and
to functions that interact strongly with the interpreter. It is always available.
#### Path
```
sys.path
sys.platform
```
The variable sys.path is a list of strings that determines the interpreter’s search path for modules. It is initialized to a default path taken from the environment variable PYTHONPATH, or from a built-in default if PYTHONPATH is not set. You can modify it using standard list operations:
```
>>> import sys
>>> sys.path.append('/ufs/guido/lib/python')
```
```
sys.path
Out[91]: 
['C:\\Program Files (x86)\\JetBrains\\PyCharm 2016.3.3\\helpers\\pydev',
 'C:\\Program Files (x86)\\JetBrains\\PyCharm 2016.3.3\\helpers\\pydev',
 'C:\\Program Files\\Anaconda3\\python35.zip']
```
```
sys.platform
Out[92]: 
'win32'
```
#### Input and output
```
sys.stdin
sys.stdout
sys.stderr
```
```
class StatusPrinter(object):
    def __init__(self, file=sys.stderr):
        self.file = file
        self.last_printed_len = 0
    
    def print_status(self, s):
        self.file.write('\r'+s+' '*max(self.last_printed_len-len(s), 0))
        self.file.flush()
        self.last_printed_len = len(s)

```
```
sp = StatusPrinter(file)
    sp.print_status(prefix + format_meter(0, total, 0))
```
####  Argument passed in python
When you run a Python module with
```
python fibo.py <arguments>
```
the code in the module will be executed, just as if you imported it, but with the __name__ set to "__main__". That means that by adding this code at the end of your module:
```
if __name__ == "__main__":
    import sys
    fib(int(sys.argv[1]))
```
you can make the file usable as a script as well as an importable module, because the code that parses the command line only runs if the module is executed as the “main” file:
```
$ python fibo.py 50
1 1 2 3 5 8 13 21 34
```
```
>>> import fibo
>>>
```

sys.argv is the list of commandline arguments passed to the Python program. 
argv represents all the items that come along via the command line input
```
sys.argv 
```

With the len(sys.argv) function you can count the number of arguments. 

If you are gonna work with command line arguments, you probably want to 
use sys.argv. 

To use sys.argv, you will first have to import the sys module.
```
import sys
print "This is the name of the script: ", sys.argv[0]
print "Number of arguments: ", len(sys.argv)
print "The arguments are: " , str(sys.argv)
```
```
python sysargv.py
This is the name of the script:  sysargv.py
Number of arguments in:  1
The arguments are:  ['sysargv.py']
```
If I run it again with additional arguments, I will get this output:
```
python sysargv.py arg1 arg2
This is the name of the script:  sysargv.py
Number of arguments in:  3
The arguments are:  ['sysargv.py', 'arg1', 'arg2']
```

####  Prompts for commands
One particular module deserves some attention: sys, which is built into every Python interpreter. The variables sys.ps1 and sys.ps2 define the strings used as primary and secondary prompts:
```
>>> import sys
>>> sys.ps1
'>>> '
>>> sys.ps2
'... '
>>> sys.ps1 = 'C> '
C> print 'Yuck!'
Yuck!
C>
```
These two variables are only defined if the interpreter is in interactive mode.

#### the dir() function
The built-in function dir() is used to find out which names a module defines. It returns a sorted list of strings:
```
>>> import fibo, sys
>>> dir(fibo)
['__name__', 'fib', 'fib2']
>>> dir(sys)  
['__displayhook__', '__doc__', '__excepthook__', '__name__', '__package__',
 '__stderr__', '__stdin__', '__stdout__', '_clear_type_cache',
 '_current_frames', '_getframe', '_mercurial', 'api_version', 'argv',
 'builtin_module_names', 'byteorder', 'call_tracing', 'callstats',
```
## Examples
### Recursively delete empty folder
```
def delete_empty_dir(dir):
    """
    Recursively delete empty folder
    """
    if os.path.exists(dir):
        if os.path.isdir(dir):
            for d in os.listdir(dir):
                path = os.path.join(dir, d)     # find the list of subfolders
                if os.path.isdir(path):
                    delete_empty_dir(path)      # recursive
        if not os.listdir(dir):
            os.rmdir(dir)
            print("remove the empty dir: {}".format(dir))
    else:
        print("Please start your performance!")  

```

