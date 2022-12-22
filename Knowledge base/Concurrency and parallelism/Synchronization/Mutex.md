A mutex (short for "mutual exclusion") is a synchronization object that allows multiple threads to access shared resources in a controlled manner. A mutex can be locked by a thread, which blocks other threads from accessing the shared resource until the mutex is unlocked. This ensures that only one thread can access the shared resource at a time, preventing race conditions and other synchronization issues.

In programming languages, mutexes are often implemented using a [[Lock]] or [[Semaphore]], which is a special type of variable that is used to control access to shared resources. When a thread acquires a lock on a mutex, it sets the value of the lock to a special value indicating that it is holding the lock. Other threads that try to acquire the lock will block until the lock is released.

```ruby
# create a shared resource (a mutex)
mutex = Mutex.new

# create a thread that acquires the mutex
thread = Thread.new do
  # acquire the mutex
  mutex.lock
  # do some work with the shared resource
  puts "Thread is working with the shared resource"
  sleep(1)
  # release the mutex
  mutex.unlock
end

# start the thread
thread.join
```

In this example, the thread acquires the mutex before accessing the shared resource, and releases the mutex when it is done. This ensures that no other thread can access the shared resource while the first thread is using it.