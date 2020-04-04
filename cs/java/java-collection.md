# Java Collection

### Iterator 

forEach, hasNext, next, remove 

```text
//ConcurrentModificationException will throw in below remove element
for (Object i : l) {
    if (condition(i)) {
        l.remove(i);
    }
}
```

```text
//to avoid ConcurrentModificationException
Iterator<String> iter = myArrayList.iterator();
while (iter.hasNext()) {
    String str = iter.next();
    if (someCondition)
        iter.remove();
}
```

### Sort

```text
// method 1
List list = new ArrayList<a> // a must implements Comparable {compareTo()}
Collections.sort(list)

// method 2
List list = new ArrayList<a> // a does not need to implement Comparable
Collections.sort(list, new comparator(){
        @override
        compare()
    }
)
    
// method 3
List list = new ArrayList<a>
list.sort(comparator)

// sort array
Arrays.sort([])
```

### Queue 

* Dequeue - LinkedList 
* PriorityQueue
  * A min-heap structure implementation  
  * Elements are stored with their natural order
  * Least element is stored at the head

### List 

ArrayList 

### Map 

```text
HashMap: Not sorted; Not safe for structural modification concurrently
---LinkedHashMap: maintain a double linked list through all entries 
SortedMap
---TreeMap: Sorted once instered in natural order
ConcurrentHashMap: java7 use segment lock. java8 extensive use of volatile and CAS(native compareAndSwapIn
WeakHashMap
--LinkedHashMap: Sorted as instersion order
```

#### HashMap

* &lt;key, value&gt; ------&gt;  Array
* key.hashCode\(\) % 15 ------&gt; Array.index
* if a.hashCode\(\) = b.hashCode\(\), then an additional list is used comparing a.key = b.key
  * So when rewriting equals\(\), must rewrite hashCode\(\) 
  * So if equals\(\) is True, hashCode\(\) must be the same.
* better to define map size before head to avoid rehashing.
  * Map map = new HashMap&lt;&gt;\(size\)

### Set

