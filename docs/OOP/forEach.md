Replace the tradition 'for' loop, operating every element in Collection / Array in simply way.

forEach() in Collection is a default method in Interface Iterable 

forEach() in Stream is a ternimal operation.
```java
collection.forEach(element -> { /* operations */ });
```

## forEach in Collection 
```java
// Example:
List<String> list = Arrays.asList("A", "B", "C");

// method 1： Lambda expression 
list.forEach(item -> System.out.println(item));

// method 2: Method reference
list.forEach(System.out::println);
```

## forEach in Map
```java
Map<Integer, String> map = Map.of(1, "One", 2, "Two");

// traversal pair of <key,value> 
map.forEach((key, value) -> 
    System.out.println(key + " = " + value)
);
```

## forEach in stream
```java
Arrays.stream(new int[]{1, 2, 3})
      .filter(n -> n > 1)
      .forEach(System.out::println);    // output:  2, 3

```