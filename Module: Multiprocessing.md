# [Multiprocessing](https://docs.python.org/2/library/multiprocessing.html)

multiprocessing is a package that supports spawning processes using an API similar to the threading module.


```
run
process.start   
process.join
```


```
from multiprocessing import Pool

def f(x):
    return x*x

if __name__ == '__main__':
    p = Pool(5)
    print(p.map(f, [1, 2, 3]))

```

To show the individual process IDs involved, here is an expanded example
```
from multiprocessing import Process
import os

def info(title):
    print(title)
    print('module name:', __name__)
    if hasattr(os, 'getppid'):  # only available on Unix
        print('parent process:', os.getppid())
    print('process id:', os.getpid())

def f(name):
    info('function f')
    print('hello', name)


if __name__ == '__main__':
    info('main line')
    p = Process(target=f, args=('bob',))
    p.start()
    p.join()
```
