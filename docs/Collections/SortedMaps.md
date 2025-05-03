# Sorted Maps and the Map Interface - Java Collections Framework

There are different implementation of the Map Interface. The first element
is identified as the "key" of the data structure.

```java
HashMap<Integer, String> hashMap = new HashMap<Integer, String>();
```

```java
LinkedHashMap<Integer, String> LhashMap = new LinkedHashMap<Integer, String>();
```

```java
TreeMap<Integer, String> treeMap = new TreeMap<Integer, String>();
```

## Import statements

To Import the following collections:

```java
import java.util.HashMap;
import java.util.Map;
import java.util.LinkedHashMap;
import java.util.TreeMap;
```

## Passing a Map Object to a method

This is how you pass a map to a method. Notice how it is possible
to pass the interface's type Map<> to the method

```java
public static void Main(String[] args){

  TreeMap<Integer, String> treeMap = new TreeMap<Integer, String>();
  testMap(treeMap);
}

public static void testMap(Map<Integer, String> map){

 // Operations
 // map.get(key);
}
```

## Cycling through the elements of a SortedMap

We can iterate over a set using a certain kind of loops:

```java
for(Integer key: map.keySet()){
  // Returns the value corresponding to that key
  String value = map.get(key);
}
```

Note that:

```java
map.keySet();
```

returns a Collection called "Set", which is itself a data structure.

## Natural Order

For strings natural order is alphabetical order, for numbers is the ordinal sorting.
You can define a natural order of your classes.
