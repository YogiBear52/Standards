# Services Concurrency

Working right with concurrency in our services is the KEY to a effective and fast service

It's important to understand that most of the execution time within services is spent on IO.

- Network IO is the the slowest action we can do. EVER.
- Disk IO

Therefore, we must make our service resources(CPU) idle while waiting to an ongoing executing IO.

Each programming language solves it differently:

## Javascript (Browser/NodeJs)

Single threaded, non-blocking-IO

- Javascript doesn't let us block any thread.
- By using only one thread, it doesn't need to manage context switch between threads
- Will block your CPU-Bound blocks - it means no one can work while CPU works hard

## C# .Net Core

- MultiThreaded lang
- A new thread is opened for each request
- It is possible to open more threads inside each thread
- It is possible to block the thread, or wait for it to finish and release it for others to use.
- Can run CPU-bound tasks without blocking other code execution

- Extreme performance potential
- Extreme bad performance potential

### Async Await

- The use of async await will release a thread to the Thread-Pool so others can use
- Async await all the way! Otherwise the thread will be blocked and the Thread-Pool will not be able to reuse it
- Don't ever use Thread.Sleep() / Task.wait / Task.Result
- Use only Task.When, which returns awaitable object
