# Java Backend Prep

## Collections

In Java, the Collections framework provides a comprehensive set of interfaces and classes to represent and manipulate collections of objects. These collections are implemented using various data structures, each tailored for different use cases in terms of performance, functionality, and specific requirements. Here are some of the main data structures available in Java Collections framework:

### 1. Lists
- **ArrayList**: Resizable array implementation of the List interface. Provides fast iteration and random access but slower insertion and deletion compared to LinkedList.
  
  ```java
  List<String> arrayList = new ArrayList<>();
  ```

- **LinkedList**: Doubly linked list implementation of the List interface. Provides fast insertion and deletion but slower random access compared to ArrayList.
  
  ```java
  List<String> linkedList = new LinkedList<>();
  ```

- **Vector**: Similar to ArrayList but synchronized (thread-safe). It's less commonly used due to its synchronized nature.

  ```java
  List<String> vector = new Vector<>();
  ```

### 2. Sets
- **HashSet**: Implements the Set interface using a hash table. Provides constant-time performance for basic operations (add, remove, contains), assuming a good hash function.
  
  ```java
  Set<String> hashSet = new HashSet<>();
  ```

- **LinkedHashSet**: Maintains insertion order of elements, in addition to HashSet behavior.
  
  ```java
  Set<String> linkedHashSet = new LinkedHashSet<>();
  ```

- **TreeSet**: Implements the Set interface using a self-balancing binary search tree (Red-Black tree). Provides sorted order of elements.
  
  ```java
  Set<String> treeSet = new TreeSet<>();
  ```

### 3. Queues
- **PriorityQueue**: Implements the Queue interface using a priority heap. Elements are ordered based on their natural ordering or a custom comparator.
  
  ```java
  Queue<String> priorityQueue = new PriorityQueue<>();
  ```

- **LinkedList**: Doubly linked list implementation of the Queue interface. Supports FIFO (First-In-First-Out) operations.
  
  ```java
  Queue<String> linkedListQueue = new LinkedList<>();
  ```

### 4. Maps
- **HashMap**: Implements the Map interface using a hash table. Provides constant-time performance for basic operations (put, get, remove), assuming a good hash function.
  
  ```java
  Map<String, Integer> hashMap = new HashMap<>();
  ```

- **LinkedHashMap**: Maintains insertion order of keys, in addition to HashMap behavior.
  
  ```java
  Map<String, Integer> linkedHashMap = new LinkedHashMap<>();
  ```

- **TreeMap**: Implements the Map interface using a self-balancing binary search tree (Red-Black tree). Provides sorted order of keys.
  
  ```java
  Map<String, Integer> treeMap = new TreeMap<>();
  ```

### 5. Deques (Double-ended Queues)
- **ArrayDeque**: Resizable-array implementation of the Deque interface. Provides fast insertion and removal at both ends.
  
  ```java
  Deque<String> arrayDeque = new ArrayDeque<>();
  ```

- **LinkedList**: Doubly linked list implementation of the Deque interface. Provides fast insertion and removal at both ends, but slower random access.
  
  ```java
  Deque<String> linkedListDeque = new LinkedList<>();
  ```

### 6. Others
- **Stack**: Implements the Stack data structure using a vector. Provides LIFO (Last-In-First-Out) operations.
  
  ```java
  Stack<String> stack = new Stack<>();
  ```

- **Hashtable**: A legacy class similar to HashMap but synchronized (thread-safe). It's less commonly used due to its synchronized nature.
  
  ```java
  Hashtable<String, Integer> hashtable = new Hashtable<>();
  ```

These data structures provide different ways to store and manipulate collections of objects in Java, each suited to different scenarios based on performance, concurrency requirements, and ordered vs. unordered access needs. Choosing the right data structure is crucial for efficient and effective programming in Java.
