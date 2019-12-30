# Java Concurrency

## java.util.concurrent 

ConcurrentMap 

ConcurrentNavigableMap 

BlockingQueue 

CountDownLatch 

CyclicBarrier 

Semaphore 

Lock 

ExecutorService 

Callable 

Future 

AtomicXXX 

## ThreadPool 

```text
Executor
--ExecutorService
----ThreadPoolExecutor
Executors.newFixedThreadPool(n) == ThreadPoolExecutor
Future
--RunnableFuture
----FutureTask
ExecutorService.submit() == RunnableFuture
```

## Synchronized VS Lock 

Synchronized: keyword, cpu intrinsic lock. Thread status is Blocked Lock: class, use CAS internally. Thread status is Waiting

## Thread communication 

Semaphore: share multiple resource. How many threads can access shared at the same time 

CyclicBarrier: All thread start when barrier reached 

CountDownLatch: A thread start when multiple thread completes \(count readch 0\)

## Note

In particular, the JMM permits compilers to allocate memory for the new Helper object and to assign a reference to that memory to the helper field before initializing the new Helper object. In other words, the compiler can reorder the write to the helper instance field and the write that initializes the Helper object \(that is, this.n = n\) so that the former occurs first. This can expose a race window during which other threads can observe a partially initialized Helper object instance.

