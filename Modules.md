# Modules
- use a handy function
Module: a way to put definitions in a file and use them in a script or in an interactive instance of the interpreter

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



### “Compiled” Python files

##  Standard Modules
Python comes with a library of standard modules, described in a separate document, the Python Library Reference

## The dir() Function
The built-in function dir() is used to find out which names a module defines. It returns a sorted list of strings


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

### first -- individual modules
Users of the package can import individual modules from the package
```
import sound.effects.echo
```
This loads the submodule sound.effects.echo. It must be referenced with its full name
```
sound.effects.echo.echofilter(input, output, delay=0.7, atten=4)
```
### second  -- submodules
An alternative way of importing the submodule is:
```
from sound.effects import echo
```
This also loads the submodule echo, and makes it available without its package prefix, so it can be used as follows:
```
echo.echofilter(input, output, delay=0.7, atten=4)
```
### third  -- function
Yet another variation is to import the desired function or variable directly
```
from sound.effects.echo import echofilter
```
Again, this loads the submodule echo, but this makes its function echofilter() directly available
```
echofilter(input, output, delay=0.7, atten=4)
```

### Note
Note that when using **from package import item**, the item can be either a submodule (or subpackage) of the package,
or some other name defined in the package, like a function, class or variable.

Contrarily, when using syntax like **import item.subitem.subsubitem**, each item except for the last must be a package; 
the last item can be a module or a package but can’t be a class or function or variable defined in the previous item.

##  Importing * From a Package
This could take a long time and importing sub-modules might have **unwanted side-effects** that should only happen when the sub-module is explicitly imported.

The only solution is for the package author to provide an explicit index of the package. 
 the file sound/effects/\__init__.py could contain the following code
```
__all__ = ["echo", "surround", "reverse"]
```

This would mean that from sound.effects import * would import the three named submodules of the sound package
Remember, there is nothing wrong with using from Package import specific_submodule! 
##  Intra-package References

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

## Packages in Multiple Directories

Packages support one more special attribute, \__path\__. This is initialized to be a list containing the name of the directory holding the package’s \__init\__.py before the code in that file is executed. 
