In programming, parallelism, refers to the ability of a system to perform multiple tasks simultaneously, by executing them at the same time using multiple cores or processors. This can be achieved through techniques such as multithreading or multiprocessing.

## In ruby

In Ruby, it is not possible to truly perform multiple tasks simultaneously on a single-core system, as Ruby is a single-threaded language. This means that a Ruby program can only execute one task at a time, even if it appears to be doing multiple things at once.

However, Ruby does provide mechanisms for achieving concurrency, such as the `Thread` class and the `Process` module, which allow you to create and manage multiple threads or processes that can be scheduled to run concurrently by the operating system. ___This can give the appearance of simultaneous execution, but in reality, the tasks are being executed one at a time, with the operating system switching between them.___

On a multi-core system, it is possible to achieve true parallelism in Ruby by using multiple threads or processes, as each core can execute a separate task at the same time. 

Here's an example of how you might use threads to perform two tasks concurrently:

```ruby
# Define a method that performs a time-consuming operation
def time_consuming_operation
  # Perform the operation
end

# Create two threads
thread1 = Thread.new do
  time_consuming_operation
end
thread2 = Thread.new do
  time_consuming_operation
end

# Wait for the threads to finish
thread1.join
thread2.join
```

Another way to achieve parallelism in Ruby is to use the `Process` module, which provides methods for creating and managing separate processes. Here's an example of how you might use processes:

```ruby
# Define a method that performs a time-consuming operation
def time_consuming_operation
  # Perform the operation
end

# Create two processes
process1 = Process.fork do
  time_consuming_operation
end
process2 = Process.fork do
  time_consuming_operation
end

# Wait for the processes to finish
Process.waitpid(process1)
Process.waitpid(process2)
```

>[!INFO]
>___However, it is important to note that Ruby's threading model is not true parallelism, as the [[Global Interpreter Lock (GIL)]] prevents multiple native threads from executing Ruby code simultaneously.___ This means that even on a multi-core system, only one thread can execute Ruby code at a time.

>[!NOTE]
>In summary, while it is not possible to truly perform multiple tasks simultaneously in Ruby on a single-core system, it is possible to achieve concurrency and parallelism on a multi-core system by using multiple threads or processes.

### True Parallelism

There are several ways to achieve true parallelism in Ruby, depending on your needs and the resources available on your system. Here are some options you might consider:

- **Using multiple processes**: One way to achieve true parallelism in Ruby is to use the `Process` module, which provides methods for creating and managing separate processes. Each process runs in a separate memory space and can execute code simultaneously on a multi-core system. ___This is a good option if you need to run tasks concurrently and don't need to share data between them.___

- **Using Ractors**: Ractors (Ruby Actors) is a new concurrency model introduced in Ruby 3.0 that allows you to create and manage lightweight, independent threads of execution called "ractors". Ractors can run concurrently on multiple cores and can communicate with each other using message passing. ___This is a good option if you need to run tasks concurrently and need to share data between them.___

- **Using threads with a GIL-releasing library**: Another option is to use the `Thread` class with a library that releases the Global Interpreter Lock (GIL) at regular intervals to allow multiple threads to execute Ruby code simultaneously. One example of such a library is `gillespie`, which is designed to work with the `Thread` class and provide true parallelism on multi-core systems. ___This is a good option if you need to run tasks concurrently and don't need to share data between them.___

>[!NOTE]
>It's worth noting that each of these approaches has its own trade-offs and limitations, and the best option for your specific use case will depend on your needs and the resources available on your system.

#### Ractors

Ractors (Ruby Actors) is a new concurrency model introduced in Ruby 3.0 that allows you to create and manage lightweight, independent threads of execution called "ractors". Ractors can run concurrently on multiple cores and can communicate with each other using message passing.

One of the main benefits of Ractors is that they allow you to achieve true parallelism on a multi-core system, without the need for explicit locking or synchronization. This is because Ractors are designed to be isolated from each other, with their own memory space and execution context. This means that Ractors can safely run concurrently without the risk of data races or other synchronization issues. 

```ruby
# Define a method that performs a time-consuming operation
def time_consuming_operation
  # Perform the operation
end

# Create two ractors
ractor1 = Ractor.new do
  time_consuming_operation
end
ractor2 = Ractor.new do
  time_consuming_operation
end

# Wait for the ractors to finish
ractor1.take
ractor2.take
```

Another of the key features of Ractors is that they bypass the Global Interpreter Lock (GIL), which is a mechanism in the Ruby interpreter that prevents multiple native threads from executing Ruby code simultaneously. This means that Ractors can achieve true parallelism on a multi-core system, without the performance limitations imposed by the GIL.

To bypass the GIL, Ractors use a different threading model than the `Thread` class, ___which is subject to the GIL___. Ractors are implemented using ___native threads___, which are managed by the operating system rather than the Ruby interpreter. This allows Ractors to run concurrently and independently of each other, ___without being subject to the GIL___.



