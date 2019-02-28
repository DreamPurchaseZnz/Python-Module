# Threading
This module constructs higher-level threading interfaces on top of lower level \_thread module
```
threading.active_count()
threading.current_thread()
threading.get_ident()
threading.enumerate()
threading.main_thread()
threading.settrace(func)
threading.setprofile(func)
threading.TIMEOUT_MAX
```
## Thread object
```
start()                  ---> once created, its activity must be started by calling -> invoke run()
                              once thread's activity is started, the thread is considered alive
                              when the run method terminates, it stops being alive
join()                   ---> This blocks the calling thread until the thread whose join() method is called is terminated
name                     ---> attribute; send to constructor
daemen thread            ---> attribute; flag meant that the entire Python program exits when the only daemon thread are left.
main thread
dummy thread             ---> alien thread; cannot be joined; always alive and daemonic
```

### Thread
```
class threading.Thread(
group=None, 
target=None,                          ---> invoked by run() method
name=None, 
args=(), 
kwargs={}, *, 
daemon=None)

```
```
start()
run()
join()                              ---> waiting until the thread terminates; 
                                         This blocks the calling thread until 
                                         the thread whose join() method is called terminates
```
### Lock objects

The class implementing primitive lock objects. Once a thread has acquired a lock, subsequent attempts to acquire it block, until it is released; any thread may release it.

```
class threading.Lock
```
Stage:Locked and unlocked
```
acquire()                    ---> change the thread to locked
release()                    ---> change the thread to unlocked
```
```
acquire(blocking=True, timeout=-1)

```
### RLock Object
### Condition Object
### Semaphore Object
### Event Object
### Timer Object
### Barrier Object





## Good explaination 
From [YOUtube](https://www.youtube.com/watch?v=cFJvBvSNeuk&list=PLGKQkV4guDKEv1DoK4LYdo2ZPLo6cyLbm)
```
import threading
import time


def sleeper(n, name):
    print("Hi am {}. Going to sleep for 5 seconds\n".format(name))
    time.sleep(n)
    print("{} has woken up from sleep.\n".format(name))

# t = threading.Thread(target=sleeper, name="thread1", args=(1, "thread_1"))
# t.start()
# t.join()

print("hello")
print("hello")

start = time.time()
threads_list = []
for i in range(5):
    t = threading.Thread(target=sleeper,
                         name="thread{}".format(i),
                         args=[5, "thread{}".format(i)])
    threads_list.append(t)
    t.start()
    print("{} has started".format(i))

for t in threads_list:
    t.join()

end = time.time()
print("time taken:{}".format(end - start))
print("All five threads have finished")


# without threading
start_ = time.time()
for i in range(5):
    print("interation {} has started".format(i))
    sleeper(5, i)

end = time.time()
print("time taken:{}".format(end-start))

```
The output
```
hello
hello
Hi am thread0. Going to sleep for 5 seconds

0 has started
Hi am thread1. Going to sleep for 5 seconds

1 has started
Hi am thread2. Going to sleep for 5 seconds

2 has started
Hi am thread3. Going to sleep for 5 seconds

3 has started
Hi am thread4. Going to sleep for 5 seconds
4 has started

thread1 has woken up from sleep.

thread0 has woken up from sleep.

thread3 has woken up from sleep.

thread2 has woken up from sleep.

thread4 has woken up from sleep.

time taken:5.002753734588623
All five threads have finished
interation 0 has started
Hi am 0. Going to sleep for 5 seconds

0 has woken up from sleep.

interation 1 has started
Hi am 1. Going to sleep for 5 seconds

1 has woken up from sleep.

interation 2 has started
Hi am 2. Going to sleep for 5 seconds

2 has woken up from sleep.

interation 3 has started
Hi am 3. Going to sleep for 5 seconds

3 has woken up from sleep.

interation 4 has started
Hi am 4. Going to sleep for 5 seconds

4 has woken up from sleep.

time taken:30.004876136779785

Process finished with exit code 0

```

