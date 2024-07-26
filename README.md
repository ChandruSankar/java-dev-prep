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

---

### Method Overloading

**Definition**: Method overloading in Java occurs when a class has more than one method with the same name, but different parameters (different type, number, or both). Overloaded methods can have different return types but must differ in their parameter lists.

**Key Points**:
- It is resolved at compile-time (compile-time polymorphism).
- It is within the same class.
- It helps to increase the readability of the program.

**Example**:
```java
public class MathOperations {
    // Overloaded method with different parameter types
    public int add(int a, int b) {
        return a + b;
    }

    // Overloaded method with different number of parameters
    public double add(double a, double b, double c) {
        return a + b + c;
    }

    // Overloaded method with different number of parameters
    public int add(int a, int b, int c) {
        return a + b + c;
    }
}

public class Test {
    public static void main(String[] args) {
        MathOperations mathOps = new MathOperations();
        
        System.out.println(mathOps.add(5, 10)); // Calls the first add method
        System.out.println(mathOps.add(5.0, 10.0, 15.0)); // Calls the second add method
        System.out.println(mathOps.add(5, 10, 15)); // Calls the third add method
    }
}
```

### Method Overriding

**Definition**: Method overriding in Java occurs when a subclass provides a specific implementation for a method that is already defined in its superclass. The method in the child class must have the same name, return type, and parameters as the method in the parent class.

**Key Points**:
- It is resolved at runtime (runtime polymorphism).
- It is used in the context of inheritance.
- The `@Override` annotation is often used to indicate that a method is overriding a superclass method.
- The overridden method can call the parent class method using the `super` keyword.

**Example**:
```java
class Animal {
    // Method to be overridden
    public void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    // Overriding the method from Animal class
    @Override
    public void makeSound() {
        System.out.println("Dog barks");
    }
}

public class Test {
    public static void main(String[] args) {
        Animal myDog = new Dog();
        myDog.makeSound(); // Calls the overridden method in Dog class
    }
}
```

**Difference Summary**:
- **Method Overloading**:
  - Same method name, different parameters.
  - Occurs within the same class.
  - Compile-time polymorphism.

- **Method Overriding**:
  - Same method name, same parameters, and return type.
  - Occurs in a subclass (inheritance).
  - Runtime polymorphism.

Both concepts are fundamental in Java programming and are widely used to implement polymorphism and enhance code flexibility and readability.

---

### Abstract Classes

**Definition**: An abstract class in Java is a class that cannot be instantiated on its own and is meant to be subclassed. It can have both abstract methods (without a body) and concrete methods (with a body).

**Key Points**:
- Abstract classes can contain both abstract and non-abstract methods.
- They can have member variables and constructors.
- They can provide a base for subclasses to build upon and implement specific behaviors.
- An abstract class is declared using the `abstract` keyword.
- A subclass must provide implementations for all abstract methods in the abstract class unless the subclass is also abstract.

**Example**:
```java
abstract class Animal {
    // Abstract method (no implementation)
    public abstract void makeSound();

    // Concrete method
    public void sleep() {
        System.out.println("This animal is sleeping");
    }
}

class Dog extends Animal {
    // Implementing the abstract method
    @Override
    public void makeSound() {
        System.out.println("Dog barks");
    }
}

public class Test {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.makeSound(); // Calls the implemented method
        myDog.sleep(); // Calls the concrete method from abstract class
    }
}
```

### Interfaces

**Definition**: An interface in Java is a reference type that can contain only abstract methods (prior to Java 8) and static constants. Starting from Java 8, interfaces can also contain default methods (with a body) and static methods. From Java 9 onwards, interfaces can contain private methods.

**Key Points**:
- All methods in an interface are abstract by default (except default and static methods).
- Interfaces cannot have instance variables but can have static constants.
- A class can implement multiple interfaces, providing a way to achieve multiple inheritance in Java.
- Interfaces are declared using the `interface` keyword.
- The implementing class must provide implementations for all abstract methods defined in the interface.

**Example**:
```java
interface Animal {
    // Abstract method
    void makeSound();

    // Default method (Java 8+)
    default void sleep() {
        System.out.println("This animal is sleeping");
    }
}

class Dog implements Animal {
    // Implementing the abstract method
    @Override
    public void makeSound() {
        System.out.println("Dog barks");
    }
}

public class Test {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.makeSound(); // Calls the implemented method
        myDog.sleep(); // Calls the default method from interface
    }
}
```

**Difference Summary**:
- **Abstract Class**:
  - Can have both abstract and concrete methods.
  - Can have member variables.
  - Can provide constructors.
  - Supports single inheritance (a class can extend only one abstract class).

- **Interface**:
  - All methods are abstract by default (prior to Java 8). From Java 8, interfaces can also have default and static methods; from Java 9, they can have private methods.
  - Cannot have instance variables but can have static constants.
  - Does not provide constructors.
  - Supports multiple inheritance (a class can implement multiple interfaces).

Both abstract classes and interfaces are used to achieve abstraction and define contracts for subclasses and implementing classes, respectively, enabling polymorphism and flexibility in Java programs.
