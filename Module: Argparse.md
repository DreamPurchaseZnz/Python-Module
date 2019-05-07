# Module: [Argparse](https://docs.python.org/3/library/argparse.html)
The argparse module makes it easy to write user-friendly command line interfaces. The program defines what arguments it requires.
 The argparse module also automatically generates help and usage messages and issues errors when users give the program invalid arguments
# Example
the following code like:
```
  from argparse import ArgumentParser
  parser = ArgumentParser()

  parser.add_argument('mode', type=str, choices=['train', 'eval', 'infer'])
  parser.add_argument('train_dir', type=str)
  parser.add_argument('--data_cfg', type=str, help='Path to dataset configuration')
  parser.add_argument('--model_type', type=str, choices=['regular', 'small'])
  parser.add_argument('--data_dir', type=str, required=True)
  parser.add_argument('--model_overrides', type=str)
  parser.add_argument('--train_ckpt_every_nsecs', type=int)
  parser.add_argument('--max_steps', type=int)
  parser.add_argument('--infer_batch_size', type=int)
  parser.add_argument('--train_summary_every_nsecs', type=int)
  parser.add_argument('--eval_dataset_name', type=str)
  parser.add_argument('--eval_wavenet_meta_fp', type=str)
  parser.add_argument('--eval_wavenet_ckpt_fp', type=str)
  parser.add_argument('--infer_dataset_name', type=str)
  parser.add_argument('--infer_ckpt_path', type=str)

  parser.set_defaults(
      mode=None,
      train_dir=None,
      model_type="regular",
      data_dir=None,
      model_overrides=None,
      train_ckpt_every_nsecs=360,
      train_summary_every_nsecs=60,
      max_steps=100000,
      infer_batch_size=1,
      eval_dataset_name=None,
      eval_wavenet_meta_fp=None,
      eval_wavenet_ckpt_fp=None,
      infer_dataset_name=None,
      infer_ckpt_path=None
      )

  args = parser.parse_args()
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
argument_default      ---> argument defaults are specified either by passing a default
allow_abbrev          ---> it recognizes abbreviations of long options.
conflict_handler      ---> it may be useful to simply override any older arguments with the same option string. To get this behavior, the 
                           value 'resolve' can be supplied to the conflict_handler= argument
add_help              ---> whether -h or --help is supplied at the command line
```
### parameter analysis
```
import argparse
parser = argparse.ArgumentParser(
    prog='DenseNet',
    usage='%(prog)s Look at the help',
    description='The program is used for building a DenseNet',
    formatter_class=argparse.RawDescriptionHelpFormatter,
    prefix_chars='--',
    allow_abbrev=True,
    conflict_handler='resolve',
    epilog='''\
          Please do not mess up this text!
          --------------------------------
          I have indented it
          exactly the way
          I want it''',)
          
# add argument    
parser.add_argument(
    '--train', action='store_true',
    help='Train the model')

args = parser.parse_args()
print(args.train)
```

```
C:\Users\CYD\Desktop\DenseNet>python args.py  -h
usage: DenseNet (-prog) Look at the help  (-usage)

The program is used for building a DenseNet (-discription)

optional arguments:
  -h, --help            show this help message and exit (-add_help)
  --train               Train the model
  --growth_rate {12,24,40}, -k {12,24,40}
                        Growth rate for every layerchoices were restricted to
                        used in paper
  --keep_prob , -kp     keep probability for dropout

         Please do not mess up this text!(-epilog)
         --------------------------------(-formatter_class)
             I have indented it
             exactly the way
             I want it

C:\Users\CYD\Desktop\DenseNet>python args.py  --tr(-allow_abbre)
True
```

### fromfile_prefix_chars
```
with open('args.txt', 'w') as fp:
...     fp.write('-f\nbar')
parser = argparse.ArgumentParser(fromfile_prefix_chars='@')
parser.add_argument('-f')
Out[22]: 
_StoreAction(option_strings=['-f'], dest='f', nargs=None, const=None, default=None, type=None, choices=None, help=None, metavar=None)
parser.parse_args(['-f', 'foo', '@args.txt'])
Out[23]: 
Namespace(f='bar')
```
### conflict_handler
it may be useful to simply override any older arguments with the same option string
```
>>> parser = argparse.ArgumentParser(prog='PROG', conflict_handler='resolve')
>>> parser.add_argument('-f', '--foo', help='old foo help')
>>> parser.add_argument('--foo', help='new foo help')
>>> parser.print_help()
usage: PROG [-h] [-f FOO] [--foo FOO]

optional arguments:
 -h, --help  show this help message and exit
 -f FOO      old foo help
 --foo FOO   new foo help
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
### name or flags
[positional argument] like foo or [optional arguments] -f, --foo shrot or long 
```
parser = argparse.ArgumentParser(prog='PROG')
>>> parser.add_argument('-f', '--foo')
>>> parser.add_argument('bar')
>>> parser.parse_args(['BAR'])
Namespace(bar='BAR', foo=None)
```
### action
```
import argparse
parser = argparse.ArgumentParser(
    prog='DenseNet',)

parser.add_argument('--a', action='store_const', const=25)
parser.add_argument('--b', action='store_true')
parser.add_argument('--c', action='append')
parser.add_argument('--d', action='append_const', const=5)
parser.add_argument('--f', action='append_const', const=4)
parser.add_argument('--g', '-g', action='count')
parser.parse_args(['--a', '--b'])
parser.parse_args('--c 1 --c 2'.split())
parser.parse_args('--d --f'.split())
parser.parse_args(['-gggg'])
```
```
parser.parse_args(['--a', '--b'])
Out[4]: 
Namespace(a=25, b=True, c=None, d=None, f=None, g=None)
parser.parse_args('--c 1 --c 2'.split())
Out[5]: 
Namespace(a=None, b=False, c=['1', '2'], d=None, f=None, g=None)
parser.parse_args('--d --f'.split())
Out[6]: 
Namespace(a=None, b=False, c=None, d=[5], f=[4], g=None)
parser.parse_args(['-gggg'])
Out[7]: 
Namespace(a=None, b=False, c=None, d=None, f=None, g=4)
```
### nargs
```
>>> parser = argparse.ArgumentParser()
>>> parser.add_argument('--foo', nargs='?', const='c', default='d')
>>> parser.add_argument('bar', nargs='?', default='d')
>>> parser.parse_args(['XX', '--foo', 'YY'])
Namespace(bar='XX', foo='YY')
>>> parser.parse_args(['XX', '--foo'])
Namespace(bar='XX', foo='c')
>>> parser.parse_args([])
Namespace(bar='d', foo='d')
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

### metavar
```
>>> parser = argparse.ArgumentParser(prog='PROG')
>>> parser.add_argument('-x', nargs=2)
>>> parser.add_argument('--foo', nargs=2, metavar=('bar', 'baz'))
>>> parser.print_help()
usage: PROG [-h] [-x X X] [--foo bar baz]

optional arguments:
 -h, --help     show this help message and exit
 -x X X
 --foo bar baz
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
parser = argparse.ArgumentParser()
parser.add_argument('foo', type=int)
Out[25]: 
_StoreAction(option_strings=[], dest='foo', nargs=None, const=None, default=None, type=<class 'int'>, choices=None, help=None, metavar=None)
parser.set_defaults(bar=42, baz='badger')
parser.parse_args(['736'])
Out[27]: 
Namespace(bar=42, baz='badger', foo=736)
```
```
ArgumentParser.get_default(dest)
```
```
>>> parser = argparse.ArgumentParser()
>>> parser.add_argument('--foo', default='badger')
>>> parser.get_default('foo')
'badger'
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
