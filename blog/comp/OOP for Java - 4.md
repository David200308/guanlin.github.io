<center> 
<h1>Object-oriented programming for Java - 4</h1> 
<h2>Java Abstract (Class & Methods)</h2>
</center>


---

## 1. Java Abstract Class

The abstract class in Java cannot be instantiated (we cannot create objects of abstract classes)

```java
abstract class Language {
  abstract void method1();
  void method2() {
    System.out.println("This is regular method");
  }
}
```



## 2. Java Abstract Method

Though abstract classes cannot be instantiated, we can create subclasses from it. We can then access members of the abstract class using the object of the subclass.

```java
abstract class Language {
  public void display() {
    System.out.println("This is Java");
  }
}

class Main extends Language {
  public static void main(String[] args) {
    Main obj = new Main();
    obj.display();
  }
}

// output
// This is Java
```

Program calling the method of the abstract class using the object *obj* (which is the object of the child class Main)



## 3. Implementing Abstract Methods

If the abstract class includes any abstract method, then all the child classes inherited from the abstract superclass must provide the implementation of the abstract method

```java
abstract class Animal {
  abstract void makeSound();
  public void eat() {
    System.out.println("I can eat.");
  }
}

class Dog extends Animal {
  public void makeSound() {
    System.out.println("Bark bark");
  }
}

class Main {
  public static void main(String[] args) {
    Dog d1 = new Dog();

    d1.makeSound();
    d1.eat();
  }
}

// output
// Bark bark
// I can eat.
```



## 4. Java Abstraction

```java
abstract class MotorBike { // create an abstract super class 
  abstract void brake(); // create an abstract method
}

class SportsBike extends MotorBike { 
  public void brake() {
    System.out.println("SportsBike Brake");
  }
}

class MountainBike extends MotorBike {
  public void brake() {
    System.out.println("MountainBike Brake");
  }
}

class Main {
  public static void main(String[] args) {
    MountainBike m1 = new MountainBike();
    m1.brake();
    SportsBike s1 = new SportsBike();
    s1.brake();
  }
}

// output:
// MountainBike Brake
// SportsBike Brake
```



