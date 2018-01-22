# time
This module provides various time-related functions. For related functionality, see also the datetime and calendar modules.

UTC is Coordinated Universal Time (formerly known as Greenwich Mean Time, or GMT). 
The acronym UTC is not a mistake but a compromise between English and French.

# [Datatime](https://docs.python.org/3.5/library/datetime.html)

The datetime module supplies classes for manipulating dates and times in both simple and complex ways.
While date and time arithmetic is supported, 
the focus of the implementation is on efficient attribute extraction for output formatting and manipulation. For related functionality, 
see also the time and calendar modules.

## Get time stamp
```
import datetime
str(datetime.datetime.utcnow())
Out[56]: 
'2018-01-22 06:02:16.003000'

datetime.datetime.now().strftime("%A, %d. %B %Y %I:%M%p")
Out[57]: 
'Monday, 22. January 2018 02:03PM'

datetime.datetime.now().isoformat()
Out[59]: 
'2018-01-22T14:03:52.696000'

``` 
