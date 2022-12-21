There are several potential issues that can arise when executing code in parallel, including:

1. [[#Race conditions]]: A race condition occurs when two or more threads try to access and modify the same shared resource concurrently, resulting in unpredictable or incorrect behavior.
2. [[#Deadlocks]]: A deadlock occurs when two or more threads are blocked, waiting for each other to release a resource that they need, resulting in a situation where none of the threads can make progress.
3. [[#Starvation]]: Starvation occurs when a thread is unable to access a shared resource that it needs, because other threads are constantly using or locking the resource.
4. [[#Priority inversion]]: Priority inversion occurs when a low-priority thread holds a lock that a high-priority thread needs, preventing the high-priority thread from making progress.

These and other issues can arise when executing code in parallel, and they can make it difficult to predict or control the behavior of a concurrent or parallel program. Therefore, it is important to carefully consider and address these issues when designing and implementing a concurrent or parallel program.

### Race conditions

```ruby
# Create a shared counter variable
counter = 0

# Create two threads that increment the counter
thread1 = Thread.new do
  10.times do
    counter += 1
    sleep(0.1)
  end
end

thread2 = Thread.new do
  10.times do
    counter += 1
    sleep(0.1)
  end
end

# Wait for the threads to finish
thread1.join
thread2.join

# Print the final value of the counter
puts "Counter: #{counter}"
```

In this example, the counter variable is shared between two threads, which both increment the counter 10 times. However, because the threads are running concurrently, there is no guarantee that the updates to the counter will be applied in the correct order, and it is possible that some updates will be lost or overwritten. This could result in an incorrect or unpredictable final value for the counter, which is an example of a race condition.

> [!Note]
> To avoid this issue, you would need to use synchronization techniques, such as locks or [[Mutex|mutexes]], to ensure that the updates to the counter are applied atomically and in the correct order. This would prevent the race condition and ensure that the final value of the counter is correct.

### Deadlocks

```ruby
# Create two locks
lock1 = Mutex.new
lock2 = Mutex.new

# Create two threads that try to acquire the locks in different order
thread1 = Thread.new do
  lock1.lock
  sleep(0.1)
  lock2.lock
  # Do some work...
  lock2.unlock
  lock1.unlock
end

thread2 = Thread.new do
  lock2.lock
  sleep(0.1)
  lock1.lock
  # Do some work...
  lock1.unlock
  lock2.unlock
end

# Wait for the threads to finish
thread1.join
thread2.join
```

In this example, the two threads both try to acquire two locks in different order. However, because the locks are shared between the threads, it is possible for the threads to deadlock each other, if thread1 acquires lock1 and then tries to acquire lock2, while thread2 acquires lock2 and then tries to acquire lock1. In this case, both threads will be blocked, waiting for the other thread to release the lock that it needs, and neither thread will be able to make progress. This is an example of a deadlock.

> [!Note]
> To avoid this issue, you would need to carefully design the locking strategy for your program, to avoid situations where threads can deadlock each other. For example, you could use a lock hierarchy, where each thread always acquires locks in the same order, to avoid deadlocks.

### Starvation

In parallel code execution, starvation refers to a situation in which a lower-priority task is not able to execute because it is continually preempted by higher-priority tasks. As a result, the lower-priority task is "starved" of the opportunity to run, potentially leading to delays or even failure in the completion of its work.

For example, consider a system with three tasks: A, B, and C. Task A has the highest priority, task B has a medium priority, and task C has the lowest priority. If task A and task B continually preempt task C, it may never be able to execute, leading to starvation.

###### Code example

	With shared resource

```ruby
# Create a shared resource
resource = Queue.new

# Create a thread that constantly adds items to the queue
producer = Thread.new do
  loop do
    resource.push(1)
    sleep(0.1)
  end
end

# Create a thread that constantly removes items from the queue
consumer = Thread.new do
  loop do
    resource.pop
    sleep(0.1)
  end
end

# Wait for the threads to finish
producer.join
consumer.join
```

In this example, the producer thread constantly adds items to a queue, while the consumer thread constantly removes items from the queue. However, because the consumer thread is slower than the producer thread, it is possible for the queue to become full, preventing the producer thread from adding new items. In this case, the producer thread will be blocked, unable to access the shared resource that it needs, and it will be unable to make progress. This is an example of starvation.

	With defferent priorities

```ruby
# create three threads with different priorities
thread_a = Thread.new do
  # do some work
  puts "Thread A is working"
  sleep(1)
end

thread_b = Thread.new do
  # do some work
  puts "Thread B is working"
  sleep(1)
end

thread_c = Thread.new do
  # do some work
  puts "Thread C is working"
  sleep(1)
end

# set the priority of the threads
thread_a.priority = 3
thread_b.priority = 2
thread_c.priority = 1

# start the threads
thread_a.join
thread_b.join
thread_c.join
```

In this example, thread A has the highest priority, thread B has a medium priority, and thread C has the lowest priority. Because the higher-priority threads (A and B) are able to preempt the lower-priority thread (C), it may never be able to execute, leading to starvation.

> [!Note]
> Starvation can have negative consequences, as it can cause lower-priority tasks to take longer to complete than they should, which can impact the overall performance of the system. To prevent starvation, many operating systems and real-time systems use techniques such as [[#Aging]] or [[#Round-robin scheduling]], which give lower-priority tasks a chance to execute periodically.

##### Aging

Aging is a technique used in some operating systems to prevent starvation by increasing the priority of a task as it gets older. The idea behind aging is that a task that has been waiting for a long time to execute is probably more important than a task that has just been created, so its priority should be increased. This gives the older task a higher chance of being able to execute, reducing the risk of starvation.

###### Round-robin scheduling

Round-robin scheduling is a scheduling algorithm in which tasks are given a fixed time slice (also known as a quantum) to execute, after which they are preempted and placed at the end of the queue to wait for their next turn. This ensures that all tasks are given a chance to execute, rather than allowing high-priority tasks to continually preempt lower-priority tasks. Round-robin scheduling can help prevent starvation, as it allows lower-priority tasks to execute periodically.


### Priority inversion

For example, consider a system with three tasks: A, B, and C. Task A has the highest priority, task B has a medium priority, and task C has the lowest priority. If task C holds a shared resource that task A needs, task A will be blocked until task C releases the resource. During this time, task B may be able to execute, even though it has a lower priority than task A. This is an example of priority inversion, as the higher-priority task (A) is being delayed by the lower-priority task (C).

###### Code example

```ruby
# create a shared resource (a mutex)
mutex = Mutex.new

# create three threads with different priorities
thread_a = Thread.new do
  # acquire the mutex
  mutex.lock
  # do some work
  puts "Thread A is working"
  sleep(1)
  # release the mutex
  mutex.unlock
end

thread_b = Thread.new do
  # acquire the mutex
  mutex.lock
  # do some work
  puts "Thread B is working"
  sleep(1)
  # release the mutex
  mutex.unlock
end

thread_c = Thread.new do
  # acquire the mutex
  mutex.lock
  # do some work
  puts "Thread C is working"
  sleep(1)
  # release the mutex
  mutex.unlock
end

# set the priority of the threads
thread_a.priority = 3
thread_b.priority = 2
thread_c.priority = 1

# start the threads
thread_a.join
thread_b.join
thread_c.join
```

In this example, thread A has the highest priority, thread B has a medium priority, and thread C has the lowest priority. However, because thread C acquires the mutex first, it holds the shared resource and blocks the other threads. As a result, thread B is able to execute before thread A, even though it has a lower priority. This is an example of priority inversion.