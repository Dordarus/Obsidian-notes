A semaphore is a synchronization object that is used to protect shared resources from being accessed by multiple threads simultaneously. A semaphore is similar to a mutex, but it allows multiple threads to acquire the semaphore concurrently, rather than allowing only a single thread to acquire it.

Semaphores are often used to control access to shared resources that are used by multiple threads. When a thread wants to access the shared resource, it acquires the semaphore, which blocks other threads from accessing the resource until the semaphore is released. This ensures that only one thread can access the resource at a time, preventing race conditions and other synchronization issues.

Here is an example of using a semaphore in Ruby:

```ruby
# create a shared resource (a mutex)
mutex = Mutex.new

# create a thread that acquires the semaphore
thread = Thread.new do
  # acquire the semaphore
  mutex.synchronize do
    # do some work with the shared resource
    puts "Thread is working with the shared resource"
    sleep(1)
  end
end

# start the thread
thread.join
```

In this example, the thread acquires the semaphore using the `synchronize` method before accessing the shared resource. This ensures that no other thread can access the shared resource while the first thread is using it. When the first thread is done, it releases the semaphore automatically.
