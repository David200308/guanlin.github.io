<center> 
<h1>Object-oriented programming for Java - 1</h1> 
<h2>Java Inheritance</h2>
</center>

---

### 1. Java Inheritance

This OOP method allowed us to create a new class on current class, which named **subclass**. 

The "extends" keyword is used to perform inheritance in Java. For example:

```java
import java.util.Scanner; // for java input

class University {
  String name;
  double gpa;
  String course;
  public void course() {
    Scanner input = new Scanner(System.in);
    System.out.print("Enter Course Code: ");
    course = input.next();
    System.out.print("Enter " + course + " GPA: ");
    gpa = input.nextDouble();
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
    david.course();
  }
}
```



### 2. Method overriding in Java Inheritance

In this method, the subclass will overrides the method in superclass. For example: 

```java
import java.util.Scanner; // for java input

class University {
  String name;
  double gpa;
  String course;
  String courseName;
  String teacher;
  public void course() {
    Scanner input = new Scanner(System.in);
    System.out.print("Enter Course Code: ");
    course = input.next();
    System.out.print("Enter " + course + " GPA: ");
    gpa = input.nextDouble();
  }
}

class Student extends University {
  @Override
  public void course() {
    Scanner input = new Scanner(System.in);
    System.out.print("Enter Course Name: ");
    course = input.next();
    System.out.print("Enter Course Code: ");
    course = input.next();
    System.out.print("Enter " + course + " GPA: ");
    gpa = input.nextDouble();
    System.out.print("Enter " + course + " Teacher Name: ");
    course = input.next();
  }
  
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
    david.course();
  }
}
```

In this example, I use override to rebuild the course() function in the second class, after running this program, only the second course() function will be called.



### 3. Super Keyword in Inheritance

In this method, use super keyword will be call the function present in the superclass. For example:

```java
import java.util.Scanner; // for java input

class University {
  String name;
  double gpa;
  String course;
  String courseName;
  String teacher;
  public void course() {
    Scanner input = new Scanner(System.in);
    System.out.print("Enter Course Code: ");
    course = input.next();
    System.out.print("Enter " + course + " GPA: ");
    gpa = input.nextDouble();
  }
}

class Student extends University {
  @Override
  public void course() {
    super.course();
    Scanner input = new Scanner(System.in);
    System.out.print("Enter " + course + " Teacher Name: ");
    course = input.next();
  }
  
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
    david.course();
  }
}
```

In this example, use super to call the course() function in the University class in the second course() function. After running, the program will be calling the first course function and printout.

### 4. Protected Members in Inheritance

In this method, use protected keyword can from subclass visit these fields and methods. For example:

```java
import java.util.Scanner; // for java input

class University {
  protected String name;
  protected double gpa;
  protected String course;
  
  protected void course() {
    Scanner input = new Scanner(System.in);
    System.out.print("Enter Course Code: ");
    course = input.next();
    System.out.println("Student Name: " + name);
    System.out.print("Enter " + course + " GPA: ");
    gpa = input.nextDouble();
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
    david.course();
    david.display();
  }
}
```















