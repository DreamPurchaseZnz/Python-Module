# Regular expression operations
regular expression matching operation

## RE Syntax
Special characters are:
```
.             ---> any character
^             ---> the start of string
$             ---> the end of string
*             ---> match 0 or more repetitions of preceding RE
+             ---> match 1 or more repetitions
?             ---> match 0 or 1 repetition
*?, +?, ??    ---> match in non-greedy or minimal fashion
{m}           ---> m copys of previous RE
{m,n}         ---> m->n copys 
{m,n}         ---> m->n copys but less one will won
\             ---> escape special character
[]            ---> a set of character, range or variance [1-9a-y]
|             ---> or
(...)         ---> match whatever regular expression inside the parentheses
(?...)
(?iLmsux)
(?:...)
(?P<name>...)
(?P=name)
(?#...)                                ---> comment
(?=...)                                ---> ... match the text
(?!...)                                ---> ... doesn't match the text
(?<=...)                               ---> a positive lookbehind assertion
(?(id/name)yes-pattern|no-pattern)
```
Example
```
>>> import re
>>> m = re.search('(?<=abc)def', 'abcdef')
>>> m.group(0)
'def'
```
Furthermore

```
\number
\A            ---> only the start of string
\b            ---> Word boundary(start tab, space or newline)
\B            ---> Not word boundary
\d            ---> Digit(0-9)
\D            ---> Not a Digit (0-9)
\s            ---> Whitespace (space, tab, newline)
\S            ---> non-whitespace (space, tab, newline)
\w            ---> word character (a-z, A-Z, 0-9, _)
\W            ---> not a word character
\Z
```
```
\a      \b      \f      \n newline
\r      \t      \v      \x
\\
```

## module contents

### re.compile(pattern, flags=0)
```
prog = re.compile(pattern)
result = prog.match(string)
```
```
result = re.match(pattern, string)
```
### re.search(pattern, string, flags=0)
### re.split(pattern, string, maxsplit=0, flags=0)
### re.findall(pattern, string, flags=0)
