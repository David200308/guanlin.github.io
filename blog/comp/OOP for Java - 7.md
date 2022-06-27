<center> 
<h1>Object-oriented programming for Java - 7</h1> 
<h2>Java Encapsulation</h2>
</center>





---

## 1. Java Encapsulation

Encapsulation refers to the bundling of fields and methods inside a single class.

It prevents outer classes from accessing and changing fields and methods of a class. This also helps to achieve **data hiding**.

### Example: (just Encapsulation, no data hiding)

```java
class Area {
  int length;
  int breadth;
  
  Area(int length, int breadth) {
    this.length = length;
    this.breadth = breadth;
  }
  
  public void getArea() {
    int area = length * breadth;
    System.out.println("Area: " + area);
	}
}

class Main {
  public static void main(String[] args) {
    Area rectangle = new Area(5, 6);
    rectangle.getArea();
  }
}

// Output:
// Area: 30
```



## 2. Data Hiding in Java Encapsulation

use access modifiers (Like: private specifier) to achieve data hiding.

### Example: (Data hiding using the private specifier)

```java
class Person {
  private int age;
  
  public int getAge() {
    return age;
  }
  
  public void setAge(int age) {
    this.age = age;
  }
}

class Main {
  public static void main(String[] args) {
    Person p1 = new Person();
    p1.setAge(18);
    int age = p1.getAge();
    System.out.println("My age is " + age);
  }
}

// output:
// My age is 18
```

### P.S.

In this example, the age varible can't access directly like: 

```java
p1.age = 18;
```

Because the age is private method, and this is unauthorized access.

