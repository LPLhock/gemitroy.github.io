# Java Collection

### Collection 

#### Iterator 

forEach, hasNext, next, remove 

ConcurrentModificationException 

#### Queue 

Dequeue - LinkedList 

PriorityQueue 

#### List 

ArrayList 

#### Map 

```text
HashMap: not safe for structural modification concurrently
---LinkedHashMap: maintain a double linked list through all entries 
SortedMap
---TreeMap 
ConcurrentHashMap: java7 use segment lock. java8 extensive use of volatile and CAS(native compareAndSwapIn
WeakHashMap
```

#### Set

