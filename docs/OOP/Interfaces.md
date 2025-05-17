# Interfaces in Java

```java
// If a class implements an Interface, then all the abstract method in this Interface defined must be implemented. Otherwise compiler report bugs. 

/*
compareTo(T other): Returns:

Negative integer if the current object is "less than" other.
Zero if the current object is "equal to" other.
Positive integer if the current object is "greater than" other.
*/

Example: 
public class Restaurant implements Comparable<Restaurant> {
        
    @Override
	public int compareTo(Restaurant o) {
		return this.getName().compareTo(o.getName());
	}

}
```

