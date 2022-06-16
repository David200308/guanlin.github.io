<center> 
<h1>Object-oriented programming for Java - 6</h1> 
<h2>Java Polymorphism</h2>
</center>




---

## 1. Java Polymorphism

Java Polymorphism use in the same entity (method or operator or object) can perform different operations in different scenarios.

```java
class Polygon {
  public void render() {
    System.out.println("Rendering Polygon...")
  }
}

class Square extends Polygon {
	public void render() {
    System.out.println("Rendering Square...")
	}
}

class Circle extends Polygon {
	public void render() {
    System.out.println("Rendering Circle...")
	}
}

class Main {
  public static void main(String[] args) {
    Square square = new Square();
    square.render();
    
    Circle circle = new Circle();
    circle.render();
  }
}

// output:
// Rendering Square...
// Rendering Circle...
```

In this example, the **`render()`** method perform different in each Class. In here we can point the **`render()`** method is **Polymorphism**.



## 2. Polymorphism using method overriding

```java
class Language {
  public void displayInfo() {
    System.out.println("Common English Language");
  }
}

class Java extends Language {
  @Override
  public void displayInfo() {
    System.out.println("Java Programming Language");
  }
}

class Main {
	public static void main(String[] args) {
    Language lang = new Language();
    lang.displayInfo();
    
    Java java = new Java();
    java.displayInfo();
  }
}

// output:
// Common English Language
// Java Programming Language
```

#### Workflow:

<img src="https://cdn.programiz.com/sites/tutorial2program/files/java-polymorphism-implementation.png" alt="Working of Java Polymorphism" style="zoom:67%;" />



## 3. Polymorphism using method overloading

```java
class Pattern {
  public void display() {
    for (int i = 0; i < 10; i++) {
      System.out.println("*");
    }
  }
  
  public void display(char symbol) {
    for (int i = 0; i < 10; i++) {
      System.out.println(symbol);
    }
  }
}

class Main {
  public static void main(String[] args) {
    Pattern pattern = new Pattern();
    pattern.display();
    System.out.println();
    pattern.display("#");
  }
}

// output:
// **********
// 
// ##########
```

#### Compare

```java
// method with no arguments
display() {
  ...
}

// method with a single char type argument
display(char symbol) {
  ...
}
```



## 3. Java Operator Overloading

### (a). For int

```java
int a = 5;
int b = 6;

// + with numbers
int sum = a + b;  // Output = 11
```

### (b). For String

```java
String first = "Java ";
String second = "Programming";

// + with strings
name = first + second;  // Output = Java Programming
```



## 4. Polymorphic Variables

**Polymorphic Variable**: if it refers to different values under different conditions.

Object variables (instance variables) represent the behavior of polymorphic variables in Java.

```java
class ProgrammingLanguage {
  public void display() {
    System.out.println("I am Programming Language.");
  }
}

class Java extends ProgrammingLanguage {
  @Override
  public void display() {
    System.out.println("I am Object-Oriented Programming Language.");
  }
}

class Main {
  public static void main(String[] args) {
    ProgrammingLanguage pl;
    
    pl = new ProgrammingLanguage();
    pl.display();

    pl = new Java();
    pl.display();
  }
}

// output:
// I am Programming Language.
// I am Object-Oriented Programming Language.
```

