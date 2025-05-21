# Factory Method

Encapsulating the **object creation** process.

Makes the code more flexible, extensible, and easy to maintain.
 
Processing a "new" objects to a method instead of using "new" directly in the code.

# Difference from Interface
Interface:
```java
    public interface Animal {
        void makeSound();
    }
    
    // in class
    public class Dog implements Animal {
        public void makeSound() {
            System.out.println("Woof!");
        }
    }

    public class Cat implements Animal {
        public void makeSound() {
            System.out.println("Meow!");
        }
    }
```

Factory Method:
```java
public class AnimalFactory {
   
    public static Animal createAnimal(String type) {
        if (type.equalsIgnoreCase("dog")) {
            return new Dog(); // 返回的是实现了 Animal 接口的类
        } else if (type.equalsIgnoreCase("cat")) {
            return new Cat();
        } else {
            throw new IllegalArgumentException("Unknown animal type");
        }
    }
}

Animal a = AnimalFactory.createAnimal("dog");
a.makeSound();      // output: "Woof!"

```

接口：定义了“能做什么”（行为规范）。

工厂方法：定义了“创建谁来做”（具体实现的选择逻辑）。

接口描述“应该有什么”，而工厂方法决定“到底要用哪一个类来实现这个接口”。

```java
    // Lab 4:
	public Municipality createOrGetMunicipality(String name, String province, Integer altitude) {
		return municipalities.computeIfAbsent(name, 
            k -> new Municipality(name, province, altitude));
	}

	public MountainHut createOrGetMountainHut(String name, Arguments...) {
		return mountainHuts.computeIfAbsent(name, 
					k -> new MountainHut(name, Arguments...));
	}
```
