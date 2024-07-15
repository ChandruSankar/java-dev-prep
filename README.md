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

---

## Stream API

Certainly! The Java Stream API provides a powerful way to work with collections of objects in a functional style, allowing operations to be performed on collections with concise and expressive syntax. Here's an overview of the functions and key concepts related to the Java Stream API:

### Key Concepts:

1. **Stream**: A sequence of elements supporting sequential and parallel aggregate operations.
   
2. **Intermediate Operations**: Operations that produce a new stream as their result, allowing further operations to be chained. Examples include `filter`, `map`, `sorted`, `distinct`, etc.
   
3. **Terminal Operations**: Operations that consume the stream and produce a result or side-effect. Examples include `forEach`, `collect`, `reduce`, `count`, etc.
   
4. **Parallel Streams**: Streams that can leverage multi-core architectures to enhance performance for bulk operations.

### Functions and Notes:

1. **Creating Streams**:

   - **From a Collection**:
     ```java
     List<String> list = Arrays.asList("a", "b", "c");
     Stream<String> streamFromList = list.stream();
     ```
   
   - **From Arrays**:
     ```java
     String[] array = {"a", "b", "c"};
     Stream<String> streamFromArray = Arrays.stream(array);
     ```
   
   - **From Static Factory Methods**:
     ```java
     Stream<String> streamOf = Stream.of("a", "b", "c");
     ```

   - **Infinite Streams** (e.g., generating infinite sequences):
     ```java
     Stream<Integer> infiniteStream = Stream.iterate(0, n -> n + 2); // Generates even numbers starting from 0
     ```
   
2. **Intermediate Operations**:

   - **filter**:
     ```java
     stream.filter(element -> element.startsWith("a"));
     ```
   
   - **map**:
     ```java
     stream.map(String::toUpperCase);
     ```
   
   - **sorted**:
     ```java
     stream.sorted();
     ```
   
   - **distinct**:
     ```java
     stream.distinct();
     ```

   - **limit** (to restrict the size of the stream):
     ```java
     stream.limit(10);
     ```
   
   - **skip** (to skip the first n elements of the stream):
     ```java
     stream.skip(5);
     ```

3. **Terminal Operations**:

   - **forEach** (performs an action for each element):
     ```java
     stream.forEach(System.out::println);
     ```
   
   - **collect** (transforms the elements of the stream into a different form):
     ```java
     List<String> collectedList = stream.collect(Collectors.toList());
     ```

   - **reduce** (performs a reduction on the elements of the stream):
     ```java
     Optional<String> reduced = stream.reduce((s1, s2) -> s1 + "#" + s2);
     ```
   
   - **count** (returns the count of elements in the stream):
     ```java
     long count = stream.count();
     ```
   
   - **anyMatch, allMatch, noneMatch** (check if any, all, or no elements match a predicate):
     ```java
     boolean anyStartsWithA = stream.anyMatch(s -> s.startsWith("a"));
     boolean allStartsWithA = stream.allMatch(s -> s.startsWith("a"));
     boolean noneStartsWithZ = stream.noneMatch(s -> s.startsWith("z"));
     ```

   - **findFirst, findAny** (find the first or any element in the stream):
     ```java
     Optional<String> firstElement = stream.findFirst();
     Optional<String> anyElement = stream.findAny();
     ```

4. **Parallel Streams**:

   - **Creating Parallel Streams**:
     ```java
     Stream<String> parallelStream = list.parallelStream();
     ```
   
   - **Performance Considerations**: Parallel streams can provide performance benefits for bulk operations on large datasets by leveraging multi-core processors. However, they require careful handling to avoid concurrency issues and ensure thread safety.

5. **Handling Exceptions**:

   - **Checked Exceptions**: Java Streams API methods do not throw checked exceptions directly. If your lambda expressions or method references throw checked exceptions, you may need to handle them explicitly within the lambda or use a try-catch block.

6. **Notes**:

   - **Immutability**: Streams do not modify the underlying data source. Instead, they provide pipelines to process data and produce results without mutating the original collection.

   - **Lazy Evaluation**: Intermediate operations are lazily evaluated, meaning they are executed only when a terminal operation is invoked. This allows for optimization and avoids unnecessary computation.

   - **Statelessness**: Operations on streams should ideally be stateless, meaning they should not depend on any mutable state or have side effects to ensure predictable behavior, especially in parallel streams.

The Java Stream API is a fundamental part of modern Java programming, enabling developers to write concise, readable, and efficient code for manipulating collections of data. Understanding these functions and concepts will help you leverage streams effectively in your Java applications.
