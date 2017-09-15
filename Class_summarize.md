# Class
Way of packaging Variables and Functions together: Attribute and Action

* Usage

the class inheritance mechanism allows **multiple base classes**, <br>
a derived class can **override** any methods of its **base class or classes**, <br>
and **a method can call the method** of a base class with the same name. <br>

## Python Scopes and Namespaces
A namespace is a mapping from names to objects.<br>
Most namespaces are currently implemented as Python dictionaries

* Namescope

Examples of namespaces are:
```
Different NameSpaces                                           Different lifetime
the set of built-in names                                      ---> When Python interpreter starts up,Never delete
the global names in a module                                   ---> when the module definition is read in,Until the python quits
the local names in a function invocation                       ---> when the function is called
                                                                    Deleted when the function returns or raises an exception
```
The important thing to know about namespaces is that there is absolutely no relation between names in different namespaces

* Lifetime
Namespaces are created at different moments and have different lifetimes,<br>
**The statements** executed by the top-level invocation of the interpreter, <br>
either read from a script file or interactively, are considered part of a module called __main__,<br>
so they have their own global namespace

* Accessible

A scope is a textual region of a Python program where a namespace is directly accessible:<br>
At any time during execution, there are at least three nested scopes whose namespaces are directly accessible:
```
the innermost scope                         ---> which is searched first, contains the local names
the scopes of any enclosing functions       ---> which are searched starting with the nearest enclosing scope, contains non-local, but 
                                                 also non-global names
the next-to-last scope                      ---> the current module’s global names
the outermost scope                         ---> (searched last) is the namespace containing built-in names
```
All variables found outside of the innermost scope are read-only except a name is declared global<br>
An attempt to write to such a variable will samplely create a **New local variable** in the intermost scope,<br>
leaving the identically named outer variable unchanged

*Assignments

It is important to realize that scopes are determined textually<br>
Assignments do not copy data — they just **bind names** to objects.<br>
The same is true for deletions: the statement del x **removes the binding** of x from the namespace referenced by the local scope

*Attribute

Attribute for any name following a dot.references to names in modules are attribute references:
```
in the expression modname.funcname, modname is a module object and funcname is an attribute of it
```
Attributes may be read-only or writable





