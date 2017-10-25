# try except
```
Exception                       
AttributeError             
IOError                  
IndexError    
KeyError    
NameError     
SyntaxError     
TypeError           
ValueError   
ZeroDivisionError         
```
```

try:
    A["blah"] = B["blah"]
except KeyError:
    pass

```
```
if "blah" in B:
    A["blah"] = B["blah"]
```

Exceptions are not conditionals
The conditional version is clearer.
That's natural: this is straightforward flow control, 
which is what conditionals are designed for, not exceptions.

```
try:  
    x = int(input('input x:'))  
    y = int(input('input y:'))  
    print('x/y = ',x/y)  
except ZeroDivisionError:
    print("ZeroDivision")  
except (TypeError,ValueError) as e:
    print(e)  
except:
    print("it's still wrong")  
else:  
    print('it work well')  
finally: 
    print("Cleaning up")  

print('I am Mt right')
```
compare the different verson of input, 
```
input x:>? 1
input y:>? 2
x/y =  0.5
it work well
Cleaning up
I am Mt right
```
```
input x:>? 2
input y:>? 0
ZeroDivision
Cleaning up
I am Mt right


```
