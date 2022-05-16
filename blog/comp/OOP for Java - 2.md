<center> 
<h1>Object-oriented programming for Java - 2</h1> 
<h2>Java Method Overriding</h2>
</center>


---

## 1. Method Overriding

In this method, use override, the display( ) function will be only call the new one, not first one.

```java
class University {
  public void display() {
    System.out.println("My name is David")
  }
}

class Student extends University {
  @Override
  public void display() {
    System.out.println("Name: " + name);
    System.out.println();
  }
}

class Main {
  public static void main(String[] args) {
    Student david = new Student();
    david.name = "David Jiang";
    david.display();
  }
}
```



## 2. Super Keyword in Java Overriding

Use super keyword can call the function in first class.

```java
class University {
  public void display() {
    System.out.println("My name is David")
  }
}

class Student extends University {
  public void display() {
    super.display();
    System.out.println("Name: " + name);
    System.out.println();
  }
}

class Main {
  public static void main(String[] args) {
    Student david = new Student();
    david.name = "David Jiang";
    david.display();
  }
}
```



## 3. Access Specifier in Overriding

The same method declared in the superclass and its subclasses can have different access specifiers.

--> P.s. Only use those access specifiers in subclasses that provide larger access than the access specifier of the superclass.

```java
class University {
  protected void display() {
    System.out.println("My name is David")
  }
}

class Student extends University {
  public void display() {
    System.out.println("Name: " + name);
    System.out.println();
  }
}

class Main {
  public static void main(String[] args) {
    Student david = new Student();
    david.name = "David Jiang";
    david.display();
  }
}
```









