# Hash Map

Maps store pair values where one member is called the "key" and the other one
is called the "value". The HashMap does not maintain order, hence, for this purpose
there's the need for SortedMaps.

```java
HashMap<Integer, String> hashMap = new HashMap<Integer, String>();
```

```java
LinkedHashMap<Integer, String> linkedhashMap = new LinkedHashMap<Integer, String>();
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

## Populating, retrieving and other operations

The put method is what populates the map

```java
map.put(5, "Five"); // 5 is a primitive type, but Java autoboxes with the respective wrapper class
```

The get method is used to retrieve values off the Map

```java
map.get(0); // I pass the index to the get method
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

## Iterating through the Map

We can iterate over a set using a foreach loop.

```java
Map.Entry<Integer, String>
```

```java
for(Map.Entry<Integer, String> entry: map.entrySet()){
  // Returns the value corresponding to that key
  String value = map.get(key);
}
```

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
