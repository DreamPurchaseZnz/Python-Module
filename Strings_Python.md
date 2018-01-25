# Strings
## Print
In principle, every computer program has to communicate with the environment or the "outside world".
To this purpose nearly every programming language has special I/O functionalities, i.e. input/output

The arguments of the print function are the following ones:
```
print(
value1, ...,                --> an arbitrary number of values
sep=' ',                    --> output is separated by blanks
end='\n',                   --> the values' end  
file=sys.stdout,            --> pass to the interpreter
flush=False)
```
The print function can print an arbitrary number of values ("value1, value2, ..."), which are separated by commas. These values are separated by blanks. 
```
print('a','b','c')            # a b c
print("a", "b", sep='')       # ab
print("a", "b", sep=':->')    # a:->b
print(192, 168, 6006,sep='.') # 192.168.6006
```
A print call is ended by a newline, as we can see in the following usage:
```
[print(i) for i in range(3)]
0
1
2
# [None, None, None]
```
To change the behavior, we can change the keyword *end*, this string will be used for ending the output of the values of  print call
```
for i in range(3):
    print(i, end=':->')   
0:->1:->2:->
```
The output of the print function is send to the standard output stream (sys.stdout) by default. By redefining the keyword parameter "file" we can send the output into a different stream e.g. sys.stderr or a file:
```
fh =  open('print.txt','w')
print('42 is the answer, but what is the question?' , file=fh)
fh.close()
```
you can see a *print.txt* file, the content is:
```
42 is the answer, but what is the question?
```

## Accessing Values in Strings

To access the substring, use the square brackets for slicing along  with the index or indices to obtain your substring

when the following code is excuted, it produces the following result.
```
var = 'Hello world'  # Hello
```
## Updating Strings
You can "update" an existing string by assigning  a variable to another string.
```
print(var[:5], 'python') # Hello python
```

## Escape Characters
Following table is a list of escape or non-printable characters that can be represented with backslash notation.
An escape character gets interpreted; in a single quoted as well as doubled quoted strings

```
Backslash notation	Hexadecimal character	Description
\a                  0x07                    Bell or alert
\b                  0x08                    Backspace
\cx                                         Control-x
\C-x                                        Control-x
\e                  0x1b                    Escape
\f                  0x0c	                Formfeed
\M-\C-x	                                    Meta-Control-x
\n                  0x0a	                Newline
\nnn                                        Octal notation, where n is in the range 0.7
\r                  0x0d                    Carriage return
\s                  0x20                    Space
\t                  0x09                    Tab
\v                  0x0b                    Vertical tab
\x                                          Character x
\xnn                                        Hexadecimal notation,
                                            where n is in the range 0.9, a.f, or A.F

```
```
\n, \t, \v, \f , \a used in python.
```

## [Multi strings in Python](https://www.smallsurething.com/multi-line-strings-in-python/)
At some points We will want to define a multi-line string and find that the obvious solution just don't feel clean.

```
template = ("This is the first line.\n"
"This is the second line.\n"
"This is the third line.")

print(template)
This is the first line.
This is the second line.
This is the third line.
```
## String Special Operators
### format- present formatted value
Perform a string [formatting operation](https://docs.python.org/3.5/library/functions.html?highlight=format#format)
The string on which this method is called can contain literal text or replacement fields delimited by braces {}.
Each replacement field contains either the numeric index of a positional argument, or the name of a keyword argument.
Returns a copy of the string where each replacement field is replaced with the string value of the corresponding argument.
[Using % and str.format for great good!](https://pyformat.info/#named_placeholders)

The general form of a standard format specifier is
```
format_spec ::=  [[fill]align][sign][#][0][width][,][.precision][type]
```
```
fill        ::=  <any character>
align       ::=  “<” | “>” | “=” | “^”
sign        ::=  “+” | “-” | ” “
width       ::=  integer
precision   ::=  integer
type        ::=  “b” | “c” | “d” | “e” | “E” | “f” | “F” | “g” | “G” | “n” | “o” | “s” | “x” | “X” | “%”
```

In most of the cases the syntax is similar to the old %-formatting, with the addition of the {} <br>
and with : used instead of %. For example, '%03.2f' can be translated to '{:03.2f}'

The meaning of the various alignment options is as follows:
```
<           ::= Left-aligned
>           ::= Right-aligned
=           ::= Padding after the sigh
^           ::= Center-aligned
```

The sign option is only valid for number types, and can be one of the following:
```
+           ::= Both positive and negative
_           ::= Negative only
space       ::= Space on positive and minus sign on negative number
```
The '#' option is only valid for integers, and only for binary, octal, or hexadecimal output.
If present, it specifies that the output will be prefixed by '0b', '0o', or '0x', respectively

The ',' option signals the use of a comma for a thousands separator.
For a locale aware separator, use the 'n' integer presentation type instead.

###  Comparison with the old %-formatting
In most of the cases the syntax is similar to the old %-formatting, 
with the addition of the {} and with : used instead of %. For example, '%03.2f' can be translated to '{:03.2f}'
The new format syntax also supports new and different options

1. Accessing arguments by 
```
position
name
attributes
items
```
2. Replacing %s and %r
```
"repr() shows quotes: {!r}; str() doesn't: {!s}".format('test1', 'test2')
```
3. Aligning the text and specifying a width:
```
>>'{:*^30}'.format('centered')  # use '*' as a fill char
>>'***********centered***********'
```
4. Replacing %+f, %-f, and % f and specifying a sign

5. Replacing %x and %o and converting the value to different bases

6. Using the comma as a thousands separator

7. Expressing a percentage
```
>>> points = 19.5
>>> total = 22
>>> 'Correct answers: {:.2%}'.format(points/total)
'Correct answers: 88.64%'
```
8. Using type-specific formatting

