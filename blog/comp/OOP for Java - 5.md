<center> 
<h1>Object-oriented programming for Java - 5</h1> 
<h2>Java Interface</h2>
</center>



---

## 1. Java Interface

To use an interface, other classes must implement it. We use the **`implements`** keyword to implement an interface.

```java
interface Polygon {
  void getArea(int length, int breadth);
}

class Rectangle implements Polygon {
  public void getArea(int length, int breadth) {
    System.out.println("The are of the rectangle is " + (length * breadth));
  }
}

class Main() {
  public static void main(String[] args) {
    Rectangle rectangle = new Rectangle();
    rectangle.getArea(5, 6)
  }
}

// output:
// The area of the rectangle is 30
```



### 1. Implementing Multiple Interfaces

#### Temple:

```java
interface A {
  // members of A
}

interface B {
  // members of B
}

class C implements A, B {
  // abstract members of A
  // abstract members of B
}
```



## 2. Extending an Interface

### 1. Extending an Interface

Similar to classes, interfaces can extend other interfaces. But the **`extends`** keyword is used for extending interfaces.

#### Temple:

```java
interface Line {
  // members of Line interface
}

// extending interface
interface Polygon extends Line {
  // members of Polygon interface
  // members of Line interface
}
```



### 2. Extending Multiple Interfaces

#### Temple:

```java
interface A {
   ...
}
interface B {
   ... 
}

interface C extends A, B {
   ...
}
```





## 3. Default Methods in Java Interfaces

To declare default methods inside interfaces, we use the **`default`** keyword.

Default methods are inherited like ordinary methods.

#### Temple:

```java
public default void getSides() {
   // body of getSides()
}
```



#### Example: (Default Method in Java Interface)

```java
interface Polygon {
  void getArea();
  
  default void getSides() {
    System.out.println("I can get sides of a polygon.")
  }
}

class Rectangle implements Polygon {
  public void getArea() {
    int length = 6;
    int breadth = 5;
    int area = length * breadth;
    System.out.println("The area of the rectangle is " + area);
  }
  
  public void getSides() {
    System.out.println("I have 4 sides.");
  }
}

class Square implements Polygon {
  public void getArea() {
    int length = 5;
    int area = length * breadth;
    System.out.println("The area of the square is " + area);
  }
}

class Main() {
  public static void main(String[] args) {
    Rectangle rectangle = new Rectangle();
    rectangle.getArea();
    rectangle.getSides(); // call class Rectangle getSides() function
    
    Square square = new Square();
    square.getArea();
    square.getSides(); // call default getSides() function
  }
}

// output:
// The area of the rectangle is 30
// I have 4 sides.
// The area of the square is 25
// I can get sides of a polygon.
```



