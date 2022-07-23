<center> 
<h1>Object-oriented programming for Java - 9</h1> 
<h2>Java Anonymous Class
</h2>
</center>





---

## 1. Java Anonymous Class

A nested class that doesn't have any name is known as an anonymous class.

- a superclass that an anonymous class extends
- an interface that an anonymous class implements



### 1.1 Anonymous Class Extending a Class

#### Example:

```java
class Polygon {
  public void display() {
    System.out.println("Inside the Polgon class");
  }
}

class AnonymousDemo {
  public void createClass() {
    Polygon p1 = new Polygon() {
      public void display() {
        System.out.println("Inside an anonymous class.")
      }
    };
    p1.display();
  }
}

class Main {
  public static void main(String[] args) {
    AnonymousDemo an = new AnonymousDemo();
    an.createClass();
  }
}

// output:
// Inside an anonymous class.
```



### 1.2 Anonymous Class Implementing an Interface

#### Example:

```java
interface Polygon {
  public void display();
}

class AnonymousDemo {
  public void createClass() {
    Polygon p1 = new Polygon() {
      public void display() {
        System.out.println("Inside an anonymous class.");
      }
    };
    p1.display();
  }
}

class Main {
  public static void main(String[] args) {
    AnonymousDemo an = new AnonymousDemo();
    an.createClass();
  }
}

// output:
// Inside an anonymous class.
```

In this example, we created an anonymous class that implements the**`Polygon`** interface.



