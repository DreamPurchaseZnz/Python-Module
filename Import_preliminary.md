# Modules
If you quit from the Python interpreter and enter it again,<br>
the definitions you have made (functions and variables) are lost.<br> 
Therefore, if you want to write a somewhat longer program, you are better off using a text editor to prepare the input for the interpreter and running it with that file as input instead. This is known as creating a script.


## The Module Search Path
When a module named spam is imported, <br>
the interpreter first searches for a built-in module with that name. <br>
If not found, it then searches for a file named spam.py in a list of directories given by the variable sys.path.<br>
sys.path is initialized from these locations:
```
the directory containing the input script (or the current directory).
PYTHONPATH (a list of directory names, with the same syntax as the shell variable PATH).
the installation-dependent default.
```

After initialization, Python programs can modify sys.path. <br>
The directory containing the script being run is placed at the beginning of the search path, ahead of the standard library path.<br>
This means that scripts in that directory will be loaded instead of modules of the same name in the library directory.<br>
This is an error unless the replacement is intended. See section Standard Modules for more information.

## Packages
Packages are a way of structuring Python’s module namespace by using “dotted module names”

For example, the module name A.B designates a submodule named B in a package named A


## Reload a module
```
from importlib import reload
reload(module)
```
