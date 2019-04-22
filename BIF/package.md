# Modules
- use a handy function
Module: a way to put definitions in a file and use them in a script or in an interactive instance of the interpreter

## Module : sys 
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


## More on modules
### Executing modules as scripts
When you run a Python module with
```
python fibo.py <arguments>
```

### The Module Search Path

 The directory containing the script being run is placed 
 at the beginning of the search path, ahead of the standard library path
 
- a built-in module with that name
- the directory containing the input script 
- PYTHONPATH (a list of directory names, with the same syntax as the shell variable PATH)
- The installation-dependent default
```
import sys
sys.path

Out[3]: 
['C:\\Program Files (x86)\\JetBrains\\PyCharm 2016.3.3\\helpers\\pydev',
 'C:\\Program Files (x86)\\JetBrains\\PyCharm 2016.3.3\\helpers\\pydev',
 'C:\\Program Files\\Anaconda3\\python35.zip',
 'C:\\Program Files\\Anaconda3\\DLLs',
 'C:\\Program Files\\Anaconda3\\lib',
 'C:\\Program Files\\Anaconda3',
 'C:\\Users\\CYD\\AppData\\Roaming\\Python\\Python35\\site-packages',
 'C:\\Program Files\\Anaconda3\\lib\\site-packages',
 'C:\\Program Files\\Anaconda3\\lib\\site-packages\\Sphinx-1.4.6-py3.5.egg',
 'c:\\users\\cyd\\src\\tqdm',
 'c:\\users\\cyd\\gym',
 'C:\\Program Files\\Anaconda3\\lib\\site-packages\\win32',
 'C:\\Program Files\\Anaconda3\\lib\\site-packages\\win32\\lib',
 'C:\\Program Files\\Anaconda3\\lib\\site-packages\\Pythonwin',
 'C:\\Program Files\\Anaconda3\\lib\\site-packages\\setuptools-27.2.0-py3.5.egg',
 'C:\\Program Files\\Anaconda3\\lib\\site-packages\\IPython\\extensions',
 'C:\\Users\\CYD\\Desktop\\Draw\\DRAW-SET',
 'C:/Users/CYD/Desktop/Draw/DRAW-SET']

```
When executing an import statement, Python looks for modules in places defined by the sys.path


## Packages

Packages are a way of structuring Python’s module namespace by using “dotted module names”.

The \__init\__.py files are required to make Python treat the directories as containing packages
```
 __init__.py files
```

Copy from [here](https://docs.python.org/3/tutorial/modules.html#packages)
```

sound/                          Top-level package
      __init__.py               Initialize the sound package
      formats/                  Subpackage for file format conversions
              __init__.py
              wavread.py
              wavwrite.py
              aiffread.py
              aiffwrite.py
              auread.py
              auwrite.py
              ...
      effects/                  Subpackage for sound effects
              __init__.py
              echo.py
              surround.py
              reverse.py
              ...
      filters/                  Subpackage for filters
              __init__.py
              equalizer.py
              vocoder.py
              karaoke.py
              ...
```

The __init__.py files are required to make Python treat the directories as containing packages,__init__.py can just be an empty file

### Individual modules
Users of the package can import individual modules from the package
```
import sound.effects.echo
```
This loads the submodule sound.effects.echo. It must be referenced with its full name
```
sound.effects.echo.echofilter(input, output, delay=0.7, atten=4)
```
#### Submodules
An alternative way of importing the submodule is:
```
from sound.effects import echo
```
This also loads the submodule echo, and makes it available without its package prefix, so it can be used as follows:
```
echo.echofilter(input, output, delay=0.7, atten=4)
```
#### Function
Yet another variation is to import the desired function or variable directly
```
from sound.effects.echo import echofilter
```
Again, this loads the submodule echo, but this makes its function echofilter() directly available
```
echofilter(input, output, delay=0.7, atten=4)
```

Note that when using **from package import item**, the item can be either a submodule (or subpackage) of the package,
or some other name defined in the package, like a function, class or variable.

Contrarily, when using syntax like **import item.subitem.subsubitem**, each item except for the last must be a package; 
the last item can be a module or a package but can’t be a class or function or variable defined in the previous item.

###  Importing * From a Package
This could take a long time and importing sub-modules might have **unwanted side-effects** that should only happen when the sub-module is explicitly imported.

The only solution is for the package author to provide an explicit index of the package. 
 the file sound/effects/\__init__.py could contain the following code
```
__all__ = ["echo", "surround", "reverse"]
```

This would mean that from sound.effects import * would import the three named submodules of the sound package
Remember, there is nothing wrong with using from Package import specific_submodule! 
###  Intra-package References

When packages are structured into subpackages (as with the sound package in the example), 
you can use **absolute imports** to refer to submodules of siblings packages

if the module sound.filters.vocoder needs to use the echo module in the sound.effects package, 
```
 from sound.effects import echo.
```
You can also write **relative imports**, with the from module import name form of import statement

These imports use leading dots to indicate the current and parent packages involved in the relative import. From the surround module for example, you might use:
```
from . import echo
from .. import formats
from ..filters import equalizer
```
Note that relative imports are based on the name of the current module.

Since the name of the main module is always "\__main\__", 
modules intended for use as the main module of a Python application must always use absolute imports.

### Packages in Multiple Directories

Packages support one more special attribute, \__path\__. This is initialized to be a list containing the name of the directory holding the package’s \__init\__.py before the code in that file is executed. 
