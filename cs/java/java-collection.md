# Java Collection

### Collection 

#### Iterator 

forEach, hasNext, next, remove 

ConcurrentModificationException 

#### Sort

```text
Collections.sort(List)
Collections.sort(llist, new comparator(){
    @override
    compare()})
Arrays.sort([])
list.sort(comparator)
```

#### Queue 

Dequeue - LinkedList 

PriorityQueue 

#### List 

ArrayList 

#### Map 

```text
HashMap: Not sorted; Not safe for structural modification concurrently
---LinkedHashMap: maintain a double linked list through all entries 
SortedMap
---TreeMap: Sorted once instered in natural order
ConcurrentHashMap: java7 use segment lock. java8 extensive use of volatile and CAS(native compareAndSwapIn
WeakHashMap
--LinkedHashMap: Sorted as instersion order
```

#### Set

