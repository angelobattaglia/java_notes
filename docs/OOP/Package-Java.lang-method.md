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

# orElse()  in Optional.java
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
//      .orElse() 会返回 Optional 中的值（如果存在），但无论如何都会先执行参数表达式。
```

## orElseThrow()    in Optional.java

```java
//  .orElseThrow() 在类型上解包了 Optional，在行为上返回 Optional 里已有的值本身（如果存在），否则抛异常。
 Person p = personRepository.findById(code)
                              .orElseThrow(NoSuchCodeException::new);
// 这里不加orElseThrow会报错，因为把 Optional<Person> 对象赋值给了 Person p对象，而orElseThrow() 是 Optional<T> 的方法，调用后返回类型就是 T（比如 Person），所以你可以直接赋值给 Person 类型变量。（解开了）
```

## isPresent() 
是 Optional 的方法，意思是“这个容器里有值吗？

