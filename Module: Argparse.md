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
## The parse_args() method
```
ArgumentParser.parse_args(args=None, namespace=None)
```
```
args                        ---> List of strings to parse. The default is taken from sys.argv
namespace                   ---> An object to take the attributes. The default is a new empty Namespace object.
```
### Option value syntax
```
1. the option and its value are passed as two separate arguments
2. long options a single command-line argument, using = to separate them like (['--foo=FOO'])
3. For short options (options only one character long), the option and its value can be concatenated like (['-xX'])
4. Several short options can be joined together, using only a single - prefix, as long as only the last option (or none of them) requires a value
```
### Invalid arguments

it exits and prints the error along with a usage message

### Arguments containing -
 -1 could either be an attempt to specify an option or an attempt to provide a positional argument
 
### Argument abbreviations (prefix matching)
allows long options to be abbreviated to a prefix

### Beyond sys.argv

### The Namespace object
Simple class used by default by parse_args() to create an object holding attributes and return it.

This class is deliberately simple, just an object subclass with a readable string representation. If you prefer to have dict-like view of the attributes, you can use the standard Python idiom, vars():
```
>>> parser = argparse.ArgumentParser()
>>> parser.add_argument('--foo')
>>> args = parser.parse_args(['--foo', 'BAR'])
>>> vars(args)
{'foo': 'BAR'}
```
assign attributes to an already existing object, rather than a new Namespace object. This can be achieved by specifying the namespace= keyword argument:
```
>>> class C:
...     pass
...
>>> c = C()
>>> parser = argparse.ArgumentParser()
>>> parser.add_argument('--foo')
>>> parser.parse_args(args=['--foo', 'BAR'], namespace=c)
>>> c.foo
'BAR'

```

## Other utilities
### Sub-commands
Many programs split up their functionality into a number of sub-commands
```
ArgumentParser.add_subparsers([title][, description][, prog][, parser_class][, action][, option_string][, dest][, help][, metavar])
```
This object has a single method, 
```
add_parser()
```
which takes a command name and any ArgumentParser constructor arguments, and returns an ArgumentParser object that can be modified as usual

### FileType objects
The FileType factory creates objects that can be passed to the type argument 
```
class argparse.FileType(mode=’r’, bufsize=-1, encoding=None, errors=None)
```
###  Argument groups
```
ArgumentParser.add_argument_group(title=None, description=None)¶
```
When an argument is added to the group, the parser treats it just like a normal argument, but displays the argument in a separate group for help messages

###  Mutual exclusion
Create a mutually exclusive group
```
ArgumentParser.add_mutually_exclusive_group(required=False)
```
### Parser defaults
```
ArgumentParser.set_defaults(**kwargs)
```
```
1. allows some additional attributes that are determined without any inspection of the command line to be added
2. parser-level defaults always override argument-level defaults
```
```
ArgumentParser.get_default(dest)
```
###  Printing help
will take care of formatting and printing any usage or error messages
```
ArgumentParser.print_usage
ArgumentParser.print_help
ArgumentParser.format_usage
ArgumentParser.format_help()
```
### Partial parsing
Sometimes a script may only parse a few of the command-line arguments, passing the remaining arguments on to another script or program
```
ArgumentParser.parse_known_args(args=None, namespace=None)
```

### Customizing file parsing
```
ArgumentParser.convert_arg_line_to_args(arg_line)
```
Arguments that are read from a file (see the fromfile_prefix_chars keyword argument to the ArgumentParser constructor) are read one argument per line. convert_arg_line_to_args() can be overridden for fancier reading
```
class MyArgumentParser(argparse.ArgumentParser):
    def convert_arg_line_to_args(self, arg_line):
        return arg_line.split()

```
### Exiting methods
```
ArgumentParser.exit(status=0, message=None)
ArgumentParser.error(message)
```
