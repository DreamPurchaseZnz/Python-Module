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
Navigate the data structure
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

## modifying the tree
    
