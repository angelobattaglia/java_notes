# Basic I/O for Java

## Input/Output on the console


## Scan

Just read an Int with Scan

```java
System.out.println("n partecipants: ");
Scanner scan = new Scanner(System.in);
int n = scan.nextInt();
```

Read an entire input and then collect the values with "split"

```java
Scanner scanner = new Scanner(System.in);
String input = scanner.next();
int words[] = input.split(' ');
```

## Buffered Reader

```java
BufferedReader in = new BufferedReader(new InputStreamReader(System.in)); 
String[] input = new String[2];     
input = in.readLine().split(" "); 
int a; 
int b; 
a = Integer.parseInt(input[0]); 
b = Integer.parseInt(input[1]); 
System.out.println("You input: " + a + " and " + b); 
```
