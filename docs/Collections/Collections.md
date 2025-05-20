# Which Java Collection to choose for which purpose

## Lists

- Store Lists of Objects
- Duplicates are allowed
- Objects remain in order
- Elements are indexed via an integer
- Checking for a particular item in list is slow
- Looking an item up by index is fast
- Iterating through lists is relatively fast
- Note: you can sort lists if you want to

```java
// If you only add or remove items at end of the list, use ArrayList
List<String> list1 = new ArrayList<String>();
```

```java
// Removing or adding items elsewhere in the list
List<String> list2 = new LinkedList<String>();
```

## Sets

- Only store unique values
- *Great for removing duplicates*
- Not Indexed, unlike lists, so there's no particular position, no positioning
- Very fast to check if a particular object exists
- If you want to use your own objects, you must implement hashCode() and equals()
- You decide whether objects are the same of not by implementing hashCode() and equals()

```java
// Order is not important and it might change: HashSet
Set<String> set1 = new HashSet<String>();
```

```java
// Sorted in Natural Order (alphabetical, numerical ascending order), must implement Comparable for custom types
Set<String> set2 = new TreeSet<String>();
```

```java
// Elements remain in the order they were added
Set<String> set3 = new LinkedHashSet<String>();
```

## Maps

- Key-value pairs (i.e. ```<String, Integer>```, ```<String, Integer, Double, String>```, ...)
- Retrieving a value by key is fast
- Iterating over maps is slow
- Maps are not optimised for iteration (if doing so, iterate through the keys)
- If you want to use your own objects as keys, you must implement hashCode() and equals()

```java
// Keys not in any particular order, and order liable to change
Map<String, String> map1 = new HashMap<String, String>();
```

```java
// Keys sorted in natural Order (alphabetical, numerical ascending order)
Map<String, String> map2 = new TreeMap<String, String>();
```

```java
// Keys remain in order added
Map<String, String> map3 = new LinkedHashMap<String, String>();
```

## The `Collection` Root Interface

```java
// A root interface more flexible (for example can change from Map to Set), 
// so if we wanna in a common use, just Collection ia enough.

Collection<Customer> customers = new ArrayList<>();

// Since it's a root interface, we can use the same way as List, Map to access, remove etc.
customers.add(s);
```

```java
//	method 'clear()' is defined in java.util.Collection interface
//  Remove all the elements in List/Set/Queue/Map(remove both Key and Value)

//  Example in lab3 WorkingHours.java

	workingHours.clear();
//  Remove first, make sure add brand new time period after.
	
```


## The return value of Collection method
```java
public Collection<String> restaurants() {
		return new LinkedList<>(restaurants.keySet());
}
	// keySet() is a method of Map Interface，return all the Key's view of Set<String>
    
	// These codes means: 
    // Transfer all the Key of 'restaurants' into a Set, and then use this Set create a new LinkedList.
	
```

