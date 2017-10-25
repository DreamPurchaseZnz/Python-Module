# Module: URLLIB
open arbitrary resources by URL(Universal Resource Locators )

urllib is a package that collects several modules for working with URLs:
```
urllib.request                                   ---> for opening and reading URLs
urllib.error                                     ---> containing the exceptions raised by urllib.request
urllib.parse                                     ---> for parsing URLs
urllib.robotparser                               ---> for parsing robots.txt files
```
## urllib.request 
The module defines functions and classes which help in opening URLs(mostly http) in a complex world.Tasks like:
```
basic and digest authentication
redirections
cookies
more

```
### urllib.request.urlopen
open the URL url, which can be either a string or a Request object
```
urllib.request.urlopen(
url,                                                  
data=None,                                         
[timeout, ]*,                                    ---> specify a time in seconds for blocking the operation like the connect attempt 
cafile=None, 
capath=None, 
cadefault=False, 
context=None
)
```
### urllib.request.Request

```
class urllib.request.Request(
url,                                             ---> a string contained a valid URL
data=None,                                       ---> a bytes object specifying additional data to send to the server
headers={},                                      ---> a dictionary; some HTTP serves only allow requests coming from common browsers
                                                                    as opposed to scripts.
origin_req_host=None, 
unverifiable=False, 
method=None)
```
### urllib.request.urlretrieve
copy a network object denoted by a URL to a local file
```
urllib.request.urlretrieve(
url, 
filename=None, 
reporthook=None, 
data=None)
```


the learning of the module will be updated soon; here are some resource from the official document which is worth to read ,
[HOWTO Fetch Internet Resources Using The urllib Package](https://docs.python.org/3.5/howto/urllib2.html#urllib-howto)
