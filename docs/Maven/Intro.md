# Maven

Maven is a build automation and project management tool for Java (and other JVM) 
projects. It resolves dependencies, downloads them, compiles your code, runs tests, 
packages artifacts, and even deploys them to repositories. You simply list the 
libraries you need (e.g. JUnit) in your POM, then, it looks in your local cache 
(usually ~/.m2/repository); if it’s not there, it downloads them from remote 
repositories (by default Maven Central) and caches them for you


## The configuration file: `pom.xml`
Describes your project in a POM (Project Object Model).
You can create a “parent” POM that aggregates several sub-modules, which means
that supports multi-module projects.

A pom.xml file sits at the root of your project.


## Maven project structure

Using a standard directory layout (src/main/java, src/test/java, etc.) means you rarely have to configure where your code lives.

Maven expects:
```shell
src/
  └── main/
      └── java/
            └── Package1/
  └── test/
      └── java/
            └── TestSuite1/
```

If you want you can omit the `src/test` repository, and just go with `src/main`. 
But, on `src/main`, I'd suggest to put a `Main.java` within the package:
```xml
<configuration>
    <!-- Fully qualified name of your entry point -->
    <mainClass>Package1.Main</mainClass>
</configuration>
```

and, on top of the `Main.java` file:
```java
package Package1;
```

having this in the `pom.xml` ensures the fact that you've got yourself an entrypoint,
a `Main`, to your application.

## Maven goals

After setting up the project structure, you can run Maven goals like `mvn clean`, `mvn compile`, `mvn test`, `mvn package`, `mvn install`.
