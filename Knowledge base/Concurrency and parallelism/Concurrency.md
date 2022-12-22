Concurrency refers to the ability of a system to perform multiple tasks simultaneously, but not necessarily at the same time. For example, a system with multiple cores can concurrently execute multiple tasks by quickly switching between them, even if the tasks are not running simultaneously.

In the context of programming languages, concurrency is often implemented using threads. A thread is a small unit of execution that can run concurrently with other threads within the same program. 

## In Ruby

For example, in the Ruby programming language, you can create a new thread by using the `Thread` class. Here's an example of how you might use this class to create a simple concurrent program:

```ruby
# Define a function that will run in a separate thread
def task
  puts "Starting task in thread #{Thread.current}"
  sleep(1) # Sleep for 1 second to simulate work
  puts "Completed task in thread #{Thread.current}"
end

# Create and start a new thread
thread = Thread.new { task }

# Wait for the thread to complete
thread.join
```

In this example, the `task` function will be run in a separate thread, concurrently with the main program. The main program will wait for the thread to complete using the `join` method. When the thread finishes, it will print a message indicating that the task has been completed.

>[!NOTE]
>There are many other ways to use concurrency in the Ruby programming language, such as by using the `ThreadPool` or `Queue` classes, or by leveraging the `parallel` gem. It's important to note that concurrency can introduce complexity to your code, and it's important to use it carefully to ensure that your program is correct and performs well.

## ThreadPool class

```ruby
# Require the 'thread' library
require 'thread'

# Define a function that will run in a separate thread
def task(id)
  puts "Starting task #{id} in thread #{Thread.current}"
  sleep(1) # Sleep for 1 second to simulate work
  puts "Completed task #{id} in thread #{Thread.current}"
end

# Create a thread pool with 3 threads
thread_pool = ThreadPool.new(3)

# Submit 10 tasks to the thread pool
10.times do |i|
  thread_pool.schedule { task(i) }
end

# Wait for all tasks to complete
thread_pool.wait_for_completion
```

In this example, the `task` function will be run in a separate thread, concurrently with the main program. The main program will create a `ThreadPool` object with 3 threads, and then submit 10 tasks to the thread pool using the `schedule` method. The main program will then wait for all of the tasks to complete using the `wait_for_completion` method.

	with Mutex locking

```ruby
# Create a mutex
mutex = Mutex.new

# Define a function that will run in a separate thread
def task(id, mutex)
  puts "Starting task #{id} in thread #{Thread.current}"
  mutex.synchronize do
    # Acquire the mutex lock
    sleep(1) # Sleep for 1 second to simulate work
  end
  puts "Completed task #{id} in thread #{Thread.current}"
end

# Create a thread pool with 3 threads
thread_pool = ThreadPool.new(3)

# Submit 10 tasks to the thread pool
10.times do |i|
  thread_pool.schedule { task(i, mutex) }
end

# Wait for all tasks to complete
thread_pool.wait_for_completion
```

In this example, the `task` function will acquire the mutex lock using the `synchronize` method before executing the critical section of code. This will prevent other threads from executing the critical section concurrently, ensuring that the shared resource is accessed safely. The `ThreadPool` class is responsible for managing the threads and scheduling the tasks, while the `Mutex` class is used to synchronize access to the shared resource.

>[!NOTE]
>The `ThreadPool` class is a convenient way to manage a group of threads and schedule tasks for them to execute. It can be useful for cases where you want to limit the number of concurrent tasks being run, or where you want to queue up tasks to be run by available threads.

## Queue class

The `Queue` class in the Ruby programming language provides a thread-safe way to pass data between threads and synchronize access to shared resources. It does this by using a mutual exclusion lock, or mutex, to ensure that only one thread can access the queue at a time.

Here's an example of how you might use the `Queue` class to synchronize access to a shared resource:

```ruby
# Create a queue
queue = Queue.new

# Define a function that will run in a separate thread
def task(id, queue)
  puts "Starting task #{id} in thread #{Thread.current}"
  # Acquire the queue lock
  queue.synchronize do
    # Access the shared resource
    sleep(1) # Sleep for 1 second to simulate work
  end
  puts "Completed task #{id} in thread #{Thread.current}"
end

# Create and start a new thread
thread = Thread.new do
  5.times do |i|
    task(i, queue)
  end
end

# Wait for the thread to complete
thread.join
```

In this example, the `task` function will acquire the queue lock using the `synchronize` method before accessing the shared resource. This will prevent other threads from accessing the shared resource concurrently, ensuring that it is accessed safely.

>[!INFO]
>The `Queue` class in the Ruby programming language uses a mutual exclusion lock, or mutex, to ensure thread safety and synchronize access to the queue. This means that you do not need to use additional synchronization mechanisms, such as the `Mutex` class, when accessing the queue.

>[!NOTE]
>You can also use the `Queue` class to pass data between threads. For example, you can use the `<<` operator to add data to the queue, and the `pop` method to retrieve data from the queue. This can be useful for communicating between threads and coordinating their work.

