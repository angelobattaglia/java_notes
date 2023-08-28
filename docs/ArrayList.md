# ArrayLists

Declaring an ArrayList. Use non-primitive type in the declaration,
i.e. wrapper classes, this is typical of Template Classes, valid
for the other Collections as well. If you need to remove items from the
middle of the start of a list, or anywhere rather than the absolute end,
you'd need to use a LinkedList.

```java
List<Integer> arrayList = new ArrayList<Integer>();
```

## Import statements

To Import the following collections:

```java
import java.util.ArrayList;
import java.util.List;
```

## Basic Operations (adding ..)

```java
// Adding
arrayList.add(3);
arrayList.add(45);
arrayList.add(929);

// Retrieving: Specify the Index
arrayList.get(0); // Index 0

// Removing: Specify the Index // Be Careful
arrayList.remove(numbers.size() - 1);
```

## Cycling through the elements of an ArrayList

We can iterate over a set using a certain kind of loops:

```java
// Indexed for-loop iteration
for(int i = 0; i < arrayList.size(); i++){
  // Printing all the elements as console output
  System.out.println(arrayList.get(i));
}

// Iteration 
for(Integer value: arrayList){
  // 
  int value = (int) arrayList.get(value);
  System.out.println(value);
}
```

Note that:

```java
map.keySet();
```

returns a Collection called "Set", which is itself a data structure.

## Passing an ArrayList Object to a method (List<> Interface)

This is how you pass a map to a method. Notice how it is possible
to pass the interface's type List<> to the method

```java
public static void Main(String[] args){

  List<Integer> arrayList = new ArrayList<Integer>();
  testArrayList(arrayList);
}

public static void testArrayList(ArrayList<Integer> arrayList){

 // Operations
 // arrayList.get(key);
}
```

## Natural Order

For strings natural order is alphabetical order, for numbers is the ordinal sorting.
You can define a natural order of your classes.

```java
Collections.sort(myList);
```
