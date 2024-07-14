
### What is concurrency in an operating system?
> Concurrency is the execution of multiple instruction sequences at the same time, occurring when there are several process threads running in parallel.
> We achieve concurrency through multithreading, multiprocessing, parallelism, and synchronization mechanisms with help of thread context switching.

### Does a single CPU system gain any benefit from multi-threading?
> No, a single CPU system does not gain any benefit from multi-threading. This is because two threads would still need to context switch for that single CPU, resulting in no performance gain.

### What is a critical section?
> In the context of concurrency, a critical section is a part of a program where shared resources are accessed and modified. Proper management of critical sections is crucial to avoid race conditions, where multiple threads or processes access shared resources simultaneously, leading to inconsistent or incorrect results.
> Here Process synchronization techniques are important because they maintain the consistency of shared data when multiple processes or threads access and modify common resources concurrently
> Ways to solve critical section and race condition:
> - Flag variable
> - Peterson's solution
> - Mutex/locks

### What is a race condition?
> A race condition occurs when two or more threads can access shared data simultaneously and attempt to change it at the same time. Because the thread scheduling algorithm can switch between threads at any moment, the order in which threads access the shared data is unpredictable. Therefore, the result of the change in data depends on the thread scheduling algorithm, with both threads 'racing' to access or modify the data.
> **Race conditions can be addressed using the following methods:**
> - **Atomic operations:** Making critical code sections atomic operations ensures they are executed in one CPU cycle.
> - **Mutual Exclusion using locks:** Locks can ensure only one thread or process accesses the critical section at a time.
> - **Semaphores:** Semaphores can be used to manage access to shared resources.


### Can a simple flag variable solve the problem of race conditions?
> No, a simple flag variable cannot solve the problem of race conditions.
> Using a simple flag to manage access to a critical section is inadequate due to the lack of atomicity, timing issues, and scalability problems. Proper synchronization mechanisms like locks, semaphores, and atomic operations should be used to effectively solve race conditions and ensure mutual exclusion.


### What is Peterson’s solution and its limitation?
> - Peterson’s solution is a classic concurrency algorithm used to avoid race conditions.  It ensures mutual exclusion between two processes (or threads) sharing a single resource or critical section. However, it is only effective for two processes or threads.
> - it is based on the idea of using two variables (turn and flag) to coordinate access to the critical section:
> - `turn`: This variable indicates whose turn it is to enter the critical section. It typically takes values 0 or 1, corresponding to each process or thread.
>-  `flag[NUM_THREADS]`:  An array of flags to indicate if a process wants to enter the critical section. For two threads, flag[0] and flag[1] are used.
> - ![image](https://github.com/user-attachments/assets/2a4c9336-e7da-4ec2-9aa8-0a0a1379ed8a)



### How do locks help in solving race conditions & What are the disadvantages of using locks?
> Locks can implement mutual exclusion by allowing only one thread or process to access the critical section at a time, thus avoiding race conditions
> **The disadvantages of using locks include:**
> - **Contention:** If one thread has acquired the lock, other threads will be busy waiting. If the thread that acquired the lock dies, other threads will wait indefinitely.
> - **Deadlocks:** Locks can lead to deadlocks if not managed properly.
> - **Debugging:** Debugging issues related to locks can be challenging.
> - **Starvation of high-priority threads:** High-priority threads might be starved if locks are not managed efficiently.



### What is a conditional variable and how does it work?
> A conditional variable is a synchronization primitive that allows a thread to wait until a certain condition becomes true before proceeding.
> It works in conjunction with a lock. When a thread enters a wait state using a conditional variable, it releases the associated lock. The thread remains suspended until another thread signals that the condition it was waiting for has been met. Upon notification, the waiting thread reacquires the lock and continues execution.

### Why use a conditional variable instead of busy waiting?
> Conditional variables are used to avoid busy waiting that comes due to locks and all, which consumes CPU resources unnecessarily. Instead of continuously checking a condition in a loop (busy waiting), threads using conditional variables can sleep efficiently until they are signaled to wake up. This reduces CPU usage and improves overall system performance.

### Explain semaphores and their types.
> **Semaphore:** Semaphores are synchronization primitives represented by an integer value. They control access to shared resources among multiple threads. There are two main types:
> - **Binary Semaphore:** Also known as mutex locks, it can have values of 0 or 1. It allows or disallows access to a single shared resource at a time, enforcing mutual exclusion.
> - **Counting Semaphore:** This type can have values ranging over an unrestricted domain. It controls access to a finite number of resource instances, allowing multiple threads to access resources concurrently based on the semaphore's count value.

### How do semaphores overcome busy waiting?
> Semaphores overcome busy waiting by modifying the wait() and signal() operations. When a thread executes wait() on a semaphore with a non-positive value, it enters a waiting state and relinquishes the CPU. The thread remains blocked until another thread increments the semaphore count with a signal() operation, waking up the waiting thread and allowing it to proceed.


### What is The Dining Philosophers' problem?
> The Dining Philosophers problem is a classic synchronization problem where five philosophers sit at a circular table with a bowl of noodles in the center. Each philosopher spends their life alternately thinking and eating. They have only two actions: picking up adjacent forks to eat and putting them down when finished.
> **Semaphore sol** The problem is solved using semaphores where each fork is represented as a binary semaphore. Philosophers use wait() operations to acquire forks and signal() operations to release them. However, this straightforward semaphore solution can lead to deadlock if all philosophers pick up their left fork simultaneously.


### What enhancements are necessary to prevent deadlock in the Dining Philosophers problem?**
> To prevent deadlock, enhancements such as:
> - **Limiting the number of philosophers:** Allow at most four philosophers to be seated at the table simultaneously.
> - **Atomic pickup of both forks:** Philosophers must pick up both forks atomically within a critical section, ensuring both are available before picking either.
> - **Odd-even rule:** Alternating philosophers pick up forks in a specific order (left-right for odd philosophers, right-left for even philosophers) to prevent circular dependency and potential deadlock.
