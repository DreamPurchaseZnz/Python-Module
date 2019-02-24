# [Beautifulsoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#find)
## Good start
```
html_doc = """
<html><head><title>The Dormouse's story</title></head>
<body>
<p class="title"><b>The Dormouse's story</b></p>

<p class="story">Once upon a time there were three little sisters; and their names were
<a href="http://example.com/elsie" class="sister" id="link1">Elsie</a>,
<a href="http://example.com/lacie" class="sister" id="link2">Lacie</a> and
<a href="http://example.com/tillie" class="sister" id="link3">Tillie</a>;
and they lived at the bottom of a well.</p>

<p class="story">...</p>
"""
```
Use bs4 to parse the html_doc
```
from bs4 import BeautifulSoup
soup = BeautifulSoup(html_doc, 'html.parser')

print(soup.prettify())
```

## Parser
```
BeautifulSoup(markup, "html.parser")
BeautifulSoup(markup, "lxml")                      ---> very fast
BeautifulSoup(markup, "lxml-xml") 
BeautifulSoup(markup, "xml") 
BeautifulSoup(markup, "html5lib")
```
## Tree - Kind of objects
Tag has a lot of attributes and methods
```
soup = BeautifulSoup('<b class="boldest">Extremely bold</b>')
tag = soup.b
type(tag)
```
## Navigate the data structure
```
soup.title
Out[20]: 
<title>The Dormouse's story</title>
```
Extract all the URLs found within a page's <a> tags
  
```
for link in soup.find_all('a'):
    print(link)
    
<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>
<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>
<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>

for link in soup.find_all('a'):
    print(link.get('href'))
    
http://example.com/elsie
http://example.com/lacie
http://example.com/tillie
```
Extract all the text from a page
```
print(soup.get_text())
```
### Going sideways
You can use .next_sibling and .previous_sibling to navigate between page elements that are on the same level of the parse tree:
```
for sibling in soup.a.next_siblings:
    print(repr(sibling))
# u',\n'
# <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>
# u' and\n'
# <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>
# u'; and they lived at the bottom of a well.'
# None

for sibling in soup.find(id="link3").previous_siblings:
    print(repr(sibling))
# ' and\n'
# <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>
# u',\n'
# <a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>
# u'Once upon a time there were three little sisters; and their names were\n'
# None


```

## search the tree
```
html_doc = """
<html><head><title>The Dormouse's story</title></head>
<body>
<p class="title"><b>The Dormouse's story</b></p>

<p class="story">Once upon a time there were three little sisters; and their names were
<a href="http://example.com/elsie" class="sister" id="link1">Elsie</a>,
<a href="http://example.com/lacie" class="sister" id="link2">Lacie</a> and
<a href="http://example.com/tillie" class="sister" id="link3">Tillie</a>;
and they lived at the bottom of a well.</p>

<p class="story">...</p>
"""

from bs4 import BeautifulSoup
soup = BeautifulSoup(html_doc, 'html.parser')
```

**find_all** method
```
find_all(
name,                      ---> position      tag with certain name
attrs,                     ---> keywords      attribute of tag
recursive,                 ---> bool          determine whether search for the descendants of tag         
string,                    ---> string        search for strings
limit,                     ---> int           limited number of tags or string
**kwargs
)
```

**find** method = find_all(title, limit=1)
```
find(
name, 
attrs, 
recursive, 
string, 
**kwargs
)
```

**find_parents and find_parent** work the way up the tree rather than the way of find_all 

```
soup.find_all("title")                            # name 
# [<title>The Dormouse's story</title>]

soup.find_all("p", "title")                                   # attrs
# [<p class="title"><b>The Dormouse's story</b></p>]

soup.find_all("a")                                                # name
# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
#  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
#  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]


soup.find_all(id="link2")                                            # keyword arguments
# [<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>]
```

### css
It’s very useful to search for a tag that has a certain CSS class, but the name of the CSS attribute, “class”, is a reserved word in Python

```
soup.find_all("a", class_="sister")                                    # css
# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
#  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
#  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]


soup.find_all("a", attrs={"class": "sister"})
# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
#  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
#  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]
```
### string
```
soup.find_all("a", string="Elsie")
# [<a href="http://example.com/elsie" class="sister" id="link1">Elsie</a>]
```

### limit
```
soup.find_all("a", limit=2)
# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
#  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>]
```

## modifying the tree
<tag class='attribute'>string<tag> 


Each tag has the attributes    
```
soup = BeautifulSoup('<b class="boldest">Extremely bold</b>', 'lxml')
tag = soup.b       ; <b class="boldest">Extremely bold</b>
tag["class"]       ;['boldest']
tag["id"]=1        ; <b class="boldest" id="1">Extremely bold</b>
del tag['id']      ; <b class="boldest">Extremely bold</b>
```
### append
```
markup = '<a href="http://example.com/">I linked to <i>example.com</i></a>'
soup= BeautifulSoup(markup, 'lxml')
tag = soup.a                         ;<a href="http://example.com/">I linked to <i>example.com</i></a>
tag.string = "New link text"         ;<a href="http://example.com/">New link text</a>
tag["href"]                          ;'http://example.com/'
```
```
soup = BeautifulSoup("<b></b>",'lxml')
original_tag = soup.b               
new_tag = soup.new_tag("a", href="http://www.example.com")
original_tag.append(new_tag)         ; <b><a href="http://www.example.com"></a></b>
new_tag.string = "Link text."        ; <b><a href="http://www.example.com">Link text.</a></b>
```


## Output
### Pretty-printing
```
markup = '<a href="http://example.com/">I linked to <i>example.com</i></a>'
soup = BeautifulSoup(markup,'lxml')

soup.prettify()
Out[54]: 
'<html>\n <body>\n  <a href="http://example.com/">\n   I linked to\n   <i>\n    example.com\n   </i>\n  </a>\n </body>\n</html>'

print(soup.prettify())
<html>
 <body>
  <a href="http://example.com/">
   I linked to
   <i>
    example.com
   </i>
  </a>
 </body>
</html>

```
