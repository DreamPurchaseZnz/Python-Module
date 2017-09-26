
Packages are a way of structuring Python’s module namespace by using “dotted module names”.
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
Note that when using from package import item, the item can be either a submodule (or subpackage) of the package,

or some other name defined in the package, like a function, class or variable.

Contrarily, when using syntax like import item.subitem.subsubitem, each item except for the last must be a package; 

the last item can be a module or a package but can’t be a class or function or variable defined in the previous item.
