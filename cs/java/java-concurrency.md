# Java Concurrency

## General

32bit JVM can have only 4G maximal memory and may faster than 64bit JVM

Long and Double read/write is not atomic in a 32 bit CPU

### Concurrency Problem

1. Visibility
2. Mutual exclusion
3. Atomic

## Threading

* Thread
* Runnable
* Callable 
* Future
* ExecutorService

### Thread Pool 

#### 原理：

1. 先判断线程池中的核心线程们是否空闲，如果空闲，就把这个新的任务指派给某一个空闲线程去执行。如果没有空闲，并且当前线程池中的核心线程数还小于 corePoolSize，那就再创建一个核心线程。
2. 如果线程池的线程数已经达到核心线程数，并且这些线程都繁忙，就把这个新来的任务放到等待队列中去。如果等待队列又满了，那么
3. 查看一下当前线程数是否到达maximumPoolSize，如果还未到达，就继续创建线程。如果已经到达了，就交给RejectedExecutionHandler来决定怎么处理这个任务。

```text
Executor
--ExecutorService
----ThreadPoolExecutor
ExecutorService es = Executors.newFixedThreadPool(n)
ExecutorService es = Executors.newScheduledThreadPool(n)
ExecutorService es = Executors.newCachedThreadPool(min, max,
        60L, TimeUnit.SECONDS, new SynchronousQueue<Runnable>())

Future
--RunnableFuture
----FutureTask
Callable<String> task = new Task()
RunnableFuture<String> future = ExecutorService.submit(task)
String result = future.get()
```

## Shared Resource Management

#### Volatile

* All update to the volatile variable will be visible to other thread
* Forbid code reorg

#### ThreadLocal

Each Thread will have a copy of a variable from main memory

Usage example: Hibernate Session

#### Synchronized VS Lock VS Atomic

* Synchronized: keyword. cpu intrinsic lock. Thread status is Blocked 
* Lock: class. More versatile, can use tryLock\(\) to avoid busy waiting.  Thread status is Waiting. Performance is the same as synchronized
* AtomicXXX: light-weight. use CAS\(low level CPU\). May use in high contention and light operation scenario

#### Popular Class in java.util.concurrent

* ConcurrentMap 
* ConcurrentNavigableMap 
* BlockingQueue 

## Thread communication 

* wait\(\)
* notify\(\)
* notifyAll\(\)

#### Popular Class in java.util.concurrent 

* CyclicBarrier: All thread start when barrier reached 
* CountDownLatch: A thread start when multiple thread completes \(count readch 0\)
* Semaphore： share multiple resource. How many threads can access shared at the same time 

## Note

In particular, the JVM permits compilers to allocate memory for the new Helper object and to assign a reference to that memory to the helper field before initializing the new Helper object. In other words, the compiler can reorder the write to the helper instance field and the write that initializes the Helper object \(that is, this.n = n\) so that the former occurs first. This can expose a race window during which other threads can observe a partially initialized Helper object instance.

乐观锁 vs 悲观锁

* 悲观锁：阻塞
* 乐观锁：非阻塞
  * Use version number. If current version is not the same as when retrieving, then update will fail.
  * CAS \(Java use CPU level CAS operation, example: Volatile/Atomic\)

