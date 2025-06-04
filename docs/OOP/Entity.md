## JPA(Java Persistance API) / Repository
```java
@OneToOne
@OneToMany
@ManyToOne
@ManyToMany
```

## Fetch Type
```java
@ManyToMany(fetch = FetchType.EAGER)
// Eager, immediately load.

@ManyToMany(fetch = FetchType.LAZY)
// Lazy, only will be loaded when we use it. 

```

```java

// Example of Entity
@Entity
class Person {
    @Id
    private String code;
    private String name;
    private String surname;
    
    // ...

}


// Save or update an entity to database.
save(entity);

// Search by ID    it's like "map.get(key)" 
findById(id);

// find all entities.
findAll();

// delete entity
delete(entity);

// delete entity by ID
deleteById(id);

// check is this ID exist
existsById(id);

count();

```
