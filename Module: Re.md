# Regular expression operations
regular expression matching operation

## RE Syntax
Special characters are:
```
.             ---> any character
^             ---> the start of string
$             ---> the end of string

# Quantifiers:
*             ---> match 0 or more repetitions of preceding RE
+             ---> match 1 or more repetitions
?             ---> match 0 or 1 repetition
*?, +?, ??    ---> match in non-greedy or minimal 
{m}           ---> m copys of previous RE
{m,n}         ---> m->n copys 
{m,n}         ---> m->n copys but less one will won

\             ---> escape special character
[]            ---> a set of character, range or variance [1-9a-y]
|             ---> or

## groups
(...)         ---> Match whatever regular expression inside the parentheses
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
```
import re
m = re.findall('abc(.)', 'abcd.efg)
-> d
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
Flags:
```
re.I          ---> case-intensive
re.L
re.M
re.S
re.U
re.X

```



### re.search(pattern, string, flags=0)
### re.split(pattern, string, maxsplit=0, flags=0)

### re.findall(pattern, string, flags=0)
find all occurrence of pattern, not just the first one
```
>>> text = "He was carefully disguised but captured quickly by police."
>>> re.findall(r"\w+ly", text)
['carefully', 'quickly']

```

# Examples
```
import re

emails = '''
CoreyMSchafer@gmail.com
corey.schafer@university.edu
corey-321-schafer@my-work.net
'''

pattern = re.compile(r'[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+')

matches = pattern.finditer(emails)

for match in matches:
    print(match)


```
```

import re

urls = '''
https://www.google.com
http://coreyms.com
https://youtube.com
https://www.nasa.gov
'''

pattern = re.compile(r'https?://(www\.)?(\w+)(\.\w+)')

subbed_urls = pattern.sub(r'\2\3', urls)

print(subbed_urls)

# matches = pattern.finditer(urls)

# for match in matches:
#     print(match.group(3))

c = re.findall(r'https?://(www\.)?(\w+)(\.\w+)', urls)
print(c)
[('www.', 'google', '.com'), ('', 'coreyms', '.com'), ('', 'youtube', '.com'), ('www.', 'nasa', '.gov')]

```





