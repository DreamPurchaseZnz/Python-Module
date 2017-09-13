# Module: Argparse
>The argparse module makes it easy to write user-friendly command line interfaces.
The program defines what arguments it requires.
 The argparse module also automatically generates help and usage messages and issues errors when users give the program invalid arguments

## Creating a parser
ArgumentParser
```
ArgumentParser(prog=None, usage=None, description=None, epilog=None, parents=[], formatter_class=argparse.HelpFormatter, prefix_chars=’-‘, fromfile_prefix_chars=None, argument_default=None, conflict_handler=’error’, add_help=True, allow_abbrev=True)
```
```
prog                  ---> determine how to display the name of the program in help messages  
description           ---> This argument gives a brief description of what the program does and how it works
usage                 ---> calculates the usage message from the arguments it contains
                           The %(prog)s format specifier is available to fill in the program name in your usage messages
epilog                ---> display additional description of the program after the description of the arguments
parents               ---> Rather than repeating the definitions of these arguments, a single parser with all the shared arguments 
formatter_class       ---> help formatting to be customized by specifying an alternate formatting class
prefix_chars          ---> Most command-line options will use - as the prefix, e.g. -f/--foo.
                            Parsers that need to support different or additional prefix characters  +f or /foo
fromfile_prefix_chars ---> when dealing with a particularly long argument lists, it may make sense to keep the list of arguments in a 
                           file rather than typing it out at the command line
argument_default      ---> argument defaults are specified either by passing a defaul
allow_abbrev          ---> it recognizes abbreviations of long options.
conflict_handler      ---> it may be useful to simply override any older arguments with the same option string. To get this behavior, the 
                           value 'resolve' can be supplied to the conflict_handler= argument
add_help              ---> whether -h or --help is supplied at the command line
```
##  Adding arguments
add_argument
```
ArgumentParser.add_argument(name or flags…[, action][, nargs][, const][, default][, type][, choices][, required][, help][, metavar][, dest])
```
```
name or flags                ---> Either a name or a list of option strings:
                                  [positional argument] like foo or [optional arguments] -f, --foo shrot or long 
action                       ---> 'store_const' 'store_true' and 'store_false' ,'append','append_const','count','help','version'          nargs                        ---> The nargs keyword argument associates a different number of command-line arguments with a single action
                                  [Number an integer]
                                  '*'. All command-line arguments present are gathered into a list
                                  '+'. Just like '*', all command-line args present are gathered into a list
                                  '?'. One argument will be consumed from the command line if possible 
                                 
default                      --->  specifies what value should be used if the command-line argument is not present
const                        --->  1.When add_argument() is called with action='store_const' or action='append_const'. These actions add                                      the const value to one of the attributes of the object returned by parse_args()
                                   2.When add_argument() is called with option strings (like -f or --foo) and nargs='?'
type                         --->  specifies the type of command-line string
choices                      --->  Some command-line arguments should be selected from a restricted set of values
required                     --->  optional arguments is required when True be specified for the argument
help                         --->  The help value is a string containing a brief description of the argument.
                                   various format specifiers to avoid repetition of things like the program name or the argument default.
                                   
metavar                      --->  generates help messages, it needs some way to refer to each expected argument
dest                         --->  optional argument actions, the value of dest is normally inferred from the option strings,dest allows 
                                   a custom attribute name to be provided
```

