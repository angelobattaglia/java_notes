# Reading a File in Java

We have three classes for reading from a Java file:

- Scanner
- FileReader
- BufferedReader

We also have a class called File that allows us to instantiate a
File Object, which is the File representation in Java.

## Reaching the file in the File System

In Eclipse, the root of the project folder is where the file system
search starts at.

If Somewhere in the file system, on Windows

```java
String fileName = "C:\\users\\username\\Desktop\\folder\\file.csv"
```

If in the src/ directory, inside the project folder, in Eclipse

```java
String fileName = "src\\file.csv"
```

If in the root of the project folder, in Eclipse

```java
String fileName = "file.csv"
```

## Reading Files with the Scanner class

Let's create a File Object, which will be a Java representation of your file.

```java
File textFile = new File(fileName);
```

Reading file using the Scanner class, I pass the file Object I want to read

```java
Scanner in = new Scanner(textFile);

// Reading the first integer of the file, supposing the first thing to read
// is a number
in.nextInt();

// Reading the new line character after the first one
in.nextLine();

// Reading it line by line
while(in.hasNextLine()){
  String line = in.nextLine();
  // Operations with the line
}

// Closing the file
in.close();
```

## Reading files with the FileReader class

```java
import java.io.*;
```

```java
File file = new File("text.txt");
```

## Reading a CSV File with the BufferedReader class

Importing the necessary libraries

```java
import java.io.*;
```

The location of the File in an Eclipse Project Folder

```java
String file = "src\\students.csv";
```

Instantiating the BufferedReader class as "null", for now

```java
BufferedReader reader = null;
```

Will be using the following to read each line of our file

```java
String line = "";
```

Let's create a Try/Catch/Finally block to manage the eventual errors.
Note: Eclipse will probably suggest its own way to managing error through
try and catch blocks. Better using the following.

```java
try{
  // Finishing instantiating our Reader
  // Withing the parentheses we pass an anonymous FileReader
  reader = new BufferedReader(new FileReader(file));
  // This while loop is going to continuosly read the next line
  // and checking if it is not "null"
  while((line = reader.readLine()) != null){

    // We specify our character, that's a String, where we want to split our line at.
    // Then, after taking all of the values of this very row in this CSV, we assing them
    // to an array of type String.
    String[] row = line.split(",");

    // Printing them on console ( yet to write )
    for(String index: row){
      System.out.println();
    }

  }
} 
// Let's catch all exceptions, since there's a moltitude of exceptions that
// could be catched, such as FileNotFoundException or IOException
catch(Exception e)
{
  // If something goes wrong, this prints the Stack Trace
  e.printStackTrace();
}
finally{

  // In programs were Scanner and BufferedReader are opened, it's good
  // practice to close them in the end. Also, it's good practice to surround them
  // with try and catch blocks.

  try{
    reader.close();
  }catch(IOException e){
    e.printStackTrace();
  }
}
```
