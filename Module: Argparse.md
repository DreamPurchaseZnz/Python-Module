# Module: [Argparse](https://docs.python.org/3/library/argparse.html)
>The argparse module makes it easy to write user-friendly command line interfaces.
The program defines what arguments it requires.
 The argparse module also automatically generates help and usage messages and issues errors when users give the program invalid arguments
# Example
the following code like:
```
import argparse

parser = argparse.ArgumentParser(description='Process some integers.')
parser.add_argument('integers', metavar='N', type=int, nargs='+',
                    help='an integer for the accumulator')
parser.add_argument('--sum', dest='accumulate', action='store_const',
                    const=sum, default=max,
                    help='sum the integers (default: find the max)')

args = parser.parse_args()
print(args.accumulate(args.integers))

```
Assuming the Python code above is saved into a file called prog.py,

it can be run at the command line and provides useful help messages:
```
$ python prog.py -h
usage: prog.py [-h] [--sum] N [N ...]

Process some integers.

positional arguments:
 N           an integer for the accumulator

optional arguments:
 -h, --help  show this help message and exit
 --sum       sum the integers (default: find the max)

```

When run with the appropriate arguments, it prints either the sum or the max of the command-line integers:

```
$ python prog.py 1 2 3 4
4

$ python prog.py 1 2 3 4 --sum
10

```

## 1. Creating a parser

ArgumentParser
```
ArgumentParser(
prog=None,                                            
usage=None,                                             
description=None, 
epilog=None, 
parents=[],
formatter_class=argparse.HelpFormatter, 
prefix_chars=’-‘,
fromfile_prefix_chars=None, 
argument_default=None, 
conflict_handler=’error’, 
add_help=True,
allow_abbrev=True)
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
##  2. Adding arguments
add_argument
```
ArgumentParser.add_argument(name or flags…[, 
action][, 
nargs][, 
const][, 
default][, 
type][, 
choices][, 
required][, 
help][, 
metavar][, 
dest])
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
dest                         --->  optional argument actions
```
### dest
For optional argument actions, the value of dest is normally inferred from name or flags(option strings),taking the first long option string and stripping away the initial -- string
```
>>> parser = argparse.ArgumentParser()
>>> parser.add_argument('-f', '--foo-bar', '--foo')
>>> parser.add_argument('-x', '-y')
>>> parser.parse_args('-f 1 -x 2'.split())
Namespace(foo_bar='1', x='2')
>>> parser.parse_args('--foo 1 -y 2'.split())
Namespace(foo_bar='1', x='2')
```
dest allows a custom attribute name to be provided:
```
>>>
>>> parser = argparse.ArgumentParser()
>>> parser.add_argument('--foo', dest='bar')
>>> parser.parse_args('--foo XXX'.split())
Namespace(bar='XXX')
```

## 3. The parse_args() method
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
```
>>> parser = argparse.ArgumentParser(prog='PROG')
>>> parser.add_argument('-x', action='store_true')
>>> parser.add_argument('-y', action='store_true')
>>> parser.add_argument('-z')
>>> parser.parse_args(['-xyzZ'])
Namespace(x=True, y=True, z='Z')

```
### Invalid arguments

it exits and prints the error along with a usage message
```
>>> parser = argparse.ArgumentParser(prog='PROG')
>>> parser.add_argument('--foo', type=int)
>>> parser.add_argument('bar', nargs='?')

>>> # invalid type
>>> parser.parse_args(['--foo', 'spam'])
usage: PROG [-h] [--foo FOO] [bar]
PROG: error: argument --foo: invalid int value: 'spam'

>>> # invalid option
>>> parser.parse_args(['--bar'])
usage: PROG [-h] [--foo FOO] [bar]
PROG: error: no such option: --bar

>>> # wrong number of arguments
>>> parser.parse_args(['spam', 'badger'])
usage: PROG [-h] [--foo FOO] [bar]
PROG: error: extra arguments found: badger

```

### Arguments containing -
 -1 could either be an attempt to specify an option or an attempt to provide a positional argument
 ```
 >>> parser = argparse.ArgumentParser(prog='PROG')
>>> parser.add_argument('-x')
>>> parser.add_argument('foo', nargs='?')

>>> # no negative number options, so -1 is a positional argument
>>> parser.parse_args(['-x', '-1'])
Namespace(foo=None, x='-1')

>>> # no negative number options, so -1 and -5 are positional arguments
>>> parser.parse_args(['-x', '-1', '-5'])
Namespace(foo='-5', x='-1')

>>> parser = argparse.ArgumentParser(prog='PROG')
>>> parser.add_argument('-1', dest='one')
>>> parser.add_argument('foo', nargs='?')

>>> # negative number options present, so -1 is an option
>>> parser.parse_args(['-1', 'X'])
Namespace(foo=None, one='X')

>>> # negative number options present, so -2 is an option
>>> parser.parse_args(['-2'])
usage: PROG [-h] [-1 ONE] [foo]
PROG: error: no such option: -2

>>> # negative number options present, so both -1s are options
>>> parser.parse_args(['-1', '-1'])
usage: PROG [-h] [-1 ONE] [foo]
PROG: error: argument -1: expected one argument
 
 ```
 
### Argument abbreviations (prefix matching)
allows long options to be abbreviated to a prefix
```
>>> parser = argparse.ArgumentParser(prog='PROG')
>>> parser.add_argument('-bacon')
>>> parser.add_argument('-badger')
>>> parser.parse_args('-bac MMM'.split())
Namespace(bacon='MMM', badger=None)
>>> parser.parse_args('-bad WOOD'.split())
Namespace(bacon=None, badger='WOOD')
>>> parser.parse_args('-ba BA'.split())
usage: PROG [-h] [-bacon BACON] [-badger BADGER]
PROG: error: ambiguous option: -ba could match -badger, -bacon

```

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
