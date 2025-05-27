# About method in java.lang

Automatically available package.

# 1 split
```java  
/* The split method belongs to the String class, which is part of the java.lang package. This package is automatically imported in all Java programs
*/

// How to use: Splits a String into an array of substrings using ":" as the delimiter.

 String[] hm = time.split(":");
//  "10:30" → ["10", "30"] 
// Example from lab3 Time.java
```

# 2 parseInt
```java
//   Converts a String to an int.

    h = Integer.parseInt(hm[0]);
 
// Transfer first element of String 'hm' to an integer. 

```

# trim()
Removes all space characters from the beginning and end of a string.
```java
    String province = fields[0].trim();  
```

# orElse() *in Optional.java
Used to handle Optional results that may be empty.

```java
    String name = optionalName.orElse("Default Name");
```
Can be used in stream API, but only used in terminal operation(because only terminal operation can return Optional object).

```java
    String result = names.stream()
                        .filter(name -> name.startsWith("A"))
                        .findFirst()            // return Optional<String>
                        .orElse("Unknown");     // Terminal 
```