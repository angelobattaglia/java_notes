# Streams (Java8)

Motivation:

> Streams are Monads, thus playing a big part in bringing functional programming to Java: In functional programming, a monad is a structure that represents computations defined as sequences of steps. A type with a monad structure defines what it means to chain operations, or nest functions of that type together.

quote: [this man](https://winterbe.com/)

## Lambda Expressions

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
.stream()
.filter(s -> s.startsWith("c"))
.map(String::toUpperCase)
.sorted()
.forEach(System.out::println);
```
