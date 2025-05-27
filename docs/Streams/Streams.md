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

return mountainHuts.values().stream().
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


Example in lab 4 (R4):
```java
    public Map<String, Long> countMunicipalitiesPerProvince() {
		return mountainHuts.values().stream()           
					.map(MountainHut::getMunicipality)
					.distinct()
					.collect(Collectors.groupingBy(Municipality::getProvince, 
								Collectors.counting()));
	}
```
        1. mountainHuts is a Map, we have to transfer it first(Because Map is not part of Collection! ).
        
        2. map in stream means transfer one data type to another data typ (Here we have MountainHut，but we need the Municipality they belongs to, so method reference and transfer).
        
        3. collect() means collect results into a Set(Natural language) or Result(Natural language).
        
        4. Collectors is a Utility Class(工具类)，defined some collectors.

**Examples Below** 


```java
    .collect(toList())          // become List
    .collect(toSet())           // become Set
    .collect(groupingBy(...))   // become Map（Accroding to the group）
```
**How to collect**
```java
public Map<Integer, List<Cell>> groupByAliveNeighborCount(Generation gen) {
        return gen.getAliveCells().stream()
                            .collect(Collectors.groupingBy(
                                Cell::countAliveNeighbors, Collectors.toList()
                            //  分组的 key ↑   @para1       ↑ 分组后的value收集方式 @para2    
                                )
                            );
}

@para1
// 每个元素（Cell）都会调用 countAliveNeighbors()，得到一个 int，用于分组。

@para2
// 分组后，每一组的元素如何收集。
// 它告诉 Java Stream：“请把分到同一组的元素放进一个 List ”
```

## Collectors.
A powerful tool.
```java
Collectors.groupingBy(classifier)        // 按条件分组
Collectors.groupingBy(classifier, downstreamCollector)  // 分组后进一步处理
// Example 
groupingBy(Employee::getDepartment)

groupingBy(Employee::getDept, summingInt(Employee::getSalary))


Collectors.partitioningBy(predicate)	//  按布尔条件分为两个分区（true/false）	
// Example
partitioningBy(e -> e.getSalary() > 5000)

Collectors.partitioningBy(predicate, downstreamCollector)	//  分区后进一步处理
// Example
partitioningBy(e -> e.getSalary() > 5000, toSet())


Collectors.mapping(mapper, downstream)	//  对元素映射后再收集	
// Example
mapping(Employee::getName, toList())

Collectors.collectingAndThen()	        //  收集后执行额外转换
// Example in Team Project
public Map<CellType, Integer> countCellsByType(Generation gen) {
        return gen.getAliveCells().stream()
                                .collect(Collectors.groupingBy(Cell::getType),
                                            Collectors.collectingAndThen(Collectors.counting(),Long::intValue));
    }
```

```java
import static java.util.stream.Collectors.*;
    //  ↑ If we do the static import, 'Collectors.' can be ignored.

    Collectors.groupingBy(...)
    // 直接 groupingBy(...) if we import static...        
    Collectors.counting()
    Collectors.mapping(...)
    // mapping(): Further transform each item in a group or aggregation.

    .map()                      // 作用于流本身
    Collectors.mapping(...)     // 用于 collect 的“嵌套映射”
    Collectors.summingInt(...)  // Calculate sum with Integer type.
    
    Collectors.summarizingInt(...)
//  Compute summary statistics for a collection of int values.
//  count, sum, min, max, average respectively. So powerful!
```

```java
/**
	 * Count the number of mountain huts per each municipality within each province.
	 * 
	 * @return a map with the province as key and, as value, a map with the
	 *         municipality as key and the number of mountain huts as value
	 */
	public Map<String, Map<String, Long>> countMountainHutsPerMunicipalityPerProvince() {
		return mountainHuts.values().stream()
					.collect(Collectors.groupingBy(h -> h.getMunicipality().getProvince(),
									Collectors.groupingBy(l -> l.getMunicipality().getName(),Collectors.counting())));}
```
