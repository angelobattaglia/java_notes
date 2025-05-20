# Streams (Java8)

Motivation:

> Streams are Monads, thus playing a big part in bringing functional programming to Java: In functional programming, a monad is a structure that represents computations defined as sequences of steps. A type with a monad structure defines what it means to chain operations, or nest functions of that type together.

quote: [this man](https://winterbe.com/)

## Lambda Expressions

'.' means:
Directly invoking method or access properties. 

```java
Class.staticMethod()
```java

'::' means:
Passing methods as parameters to functional interfaces.
将[方法]作为[参数]传递给函数式接口
It is a short form of Lambda.

```java
stream.map(String::toUpperCase)
```

# Basic Concepts of stream
1. Source operations:
Create: Generate a stream from a data source (collection, array, etc.).
```java
Stream<String> stream = list.stream();
// or
Stream<String> parallelStream = list.parallelStream(); 
```

2. Intermediate Operations: 
Define data processing logic (such as filtering, mapping).
```java
.filter(n -> n % 2 == 0)  // 保留偶数
.map(String::toUpperCase)  // 转换为大写
.flatMap(List::stream)  // 扁平化为单个流
.distinct()
.sorted()                   // natural order
.skip(5)    // 跳过前5个（0-4）
.limit(3)   // 取接下来的3个
```

3. Terminal Operations:
Trigger the actual calculation and generate results.
```java
.collect(Collectors.toList());      
.forEach(System.out::println);
.reduce(0, Integer::sum);
.findFirst();
.findAny();
.max(Integer::compare);
.count();
.min();
```

To put it simple, see how the following code gets
shortened at each step:

Step 1

```java
List<String> names = Arrays.asList("peter", "anna", "mike", "xenia");
Collections.sort(names, new Comparator<String>() {
@Override
public int compare(String a, String b) {
return b.compareTo(a);
}
});
```

Step 2

```java
Collections.sort(names, (String a, String b) -> {
return b.compareTo(a);
});
```

Step 3

```java
Collections.sort(names, (String a, String b) -> b.compareTo(a));
```

Step 4

```java
Collections.sort(names, (a, b) -> b.compareTo(a));
```

## Imports

```java
```

example

```java
List<String> myList =
Arrays.asList("a1", "a2", "b1", "c2", "c1");

myList
.stream()                            // 1. Create operation
.filter(s -> s.startsWith("c"))      // 2. Middle operations
.map(String::toUpperCase)
.sorted()
.forEach(System.out::println);       // 3. Terminal operation
```

Some Characteristics:

1. Non-Reusability
A Stream can be consumed only once.

2. Lazy Evaluation (Delayed Execution)
 Actual computation happens when a terminal operation (e.g., collect, forEach) is invoked.

3. Parallel Processing
Streams can leverage multicore processors via parallel execution.
