<center> 
<h1>Object-oriented programming for Java - 3</h1> 
<h2>Java Super</h2>
</center>


---

## 1. Access Overridden Methods of the superclass

Use super.display if overridden method display() of superclass Animal needs to be called.

```java
class Animal {
  public void display() {
    System.out.println("I am an animal");
  }
}

class Dog extends Animal {
  @Override
  public void display() {
    System.out.println("I am a dog");
  }
  public void printMessage() {
    display();
    super.display(); // use super.display() to call the Animal class display() function
  }
}

class Main {
  public static void main(String[] args) {
    Dog dog1 = new Dog();
    dog1.printMessage();
  }
}

// ouput:
// I am a dog
// I am an animal
```

### Program Work Process:

<img src="https://cdn.programiz.com/sites/tutorial2program/files/call-superclass-method.png" alt="image-super_keyword_1" style="zoom:50%;" />



## 2. Access Attributes of the Superclass

```java
class Animal {
  protected String type = "animal";
}
class Dog extends Animal {
  public String type = "mammal";
  
  public void printType() {
    System.out.println("I am a " + type);
    System.out.println("I am an " + super.type);
  }
}

class Main {
  public static void main(String[] args) {
    Dog dog1 = new Dog();
    dog1.printType();
  }
}

// ouput:
// I am a mammal
// I am an animal
```



## 3. Use of super() to access superclass constructor

### (a) Use of super()

```java
class Animal {
  Animal() {
    System.out.println("I am an animal");
  }
}

class Dog extends Animal {
  Dog() {
    super();
    System.out.println("I am a dog");
  }
}

class Main {
  public static void main(String[] args) {
    Dog dog1 = new Dog();
  }
}

// ouput:
// I am an animal
// I am a dog
```

### Program Work Process:

<img src="https://cdn.programiz.com/sites/tutorial2program/files/super%28%29-example.png" alt="image-super_keyword_1" style="zoom:60%;" />



### (b) Call Parameterized Constructor Using super()

```java
class Animal {
  Animal() {
    System.out.println("I am an animal");
  }
  Animal(String type) {
    System.out.println("Type: "+type);
  }
}

class Dog extends Animal {
  Dog() {
    super("Animal"); // transfer "Animal" to Animal(String type) this function
    // super(); // if use super(), will be call the Animal() this function
    System.out.println("I am a dog");
  }
}

class Main {
  public static void main(String[] args) {
    Dog dog1 = new Dog();
  }
}

// ouput:
// Type: Animal
// I am a dog
```

### Program Work Process:

<img src="https://cdn.programiz.com/sites/tutorial2program/files/parameterized-super-example.png" alt="image-super_keyword_1" style="zoom:55%;" />





