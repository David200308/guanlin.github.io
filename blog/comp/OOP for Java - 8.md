<center> 
<h1>Object-oriented programming for Java - 8</h1> 
<h2>Java Nested and Inner Class</h2>
</center>




---

## 1. Java Non-Static Nested Class (Inner Class)

### 1.1 Inner Class

#### Example:

```java
class CPU {
	double price;
  class Processor {
    double core;
    String manufacturer;
    
    double getCache() {
      return 4.3;
    }
  }
  protected class RAM {
    double memory;
    String manufacturer;
    
    double getClockSpeed() {
      return 5.5;
    }
  }
}

public class Main {
  public static void main(String[] args) {
    CPU cpu = new CPU();
    CPU.Processor processor = cpu.new Processor();
    CPU.RAM ram = CPU.new RAM();
    
    System.out.println("Processor Cache = " + processor.getCache());
    System.out.println("Ram Clock speed = " + ram.getClockSpeed());
  }
}

// output:
// Processor Cache = 4.3
// Ram Clock speed = 5.5
```

In this example, there are two nested classes: **`Processor`** and **`RAM`** inside the outer class:**`CPU`**

```java
CPU.Processor processor = cpu.new Processor();
CPU.RAM ram = CPU.new RAM();
```

(Inner Classes Create)



### 1.2 Accessing Members of Outer Class within Inner Class (Accessing Members)

```java
class Car {
  String CarName;
  String CarType;
  
  public Car(String name, String type) {
    this.CarName = name;
    this.CarType = type;
  }
  
  private String getCarName() {
    return this.CarName;
  }
  
  class Engine {
    String EngineType;
    void setEngine() {
      if (Car.this.CarType.equals("4WD")) {
        if (Car.this.getCarName().equals("Crysler")) {
          this.EngineType = "Smaller";
        } else {
          this.EngineType = "Bigger";
        }
      } else {
        this.EngineType = "Bigger";
      }
    }
    String getEngineType() {
      return this.EngineType;
    }
  }
}

public class Main {
  public static void main(String[] args) {
    Car car = new Car("Mazda", "8WD");
    Car.Engine engine = new.Car Engine();
    engine.setEngine();
    System.out.println("Engine Type for 8WD = " + engine.getEngineType());
  }
}

// output:
// Engine Type for 8WD = Bigger
```

In this example, code are using  **`this`** keyword to access the CarType variable of the outer class.



## 2. Java Static Nested Class

In Java, we can also define a **`static`** class inside another class.

A static nested class cannot access the member variables of the outer class.

### 2.1 Static Inner Class

```java
class MotherBoard {
  static class USB {
    int usb2 = 2;
    int usb3 = 1;
    int getTotalPorts() {
      return usb2 + usb3;
    }
  }
}

public class Main {
  public static void main(String[] args) {
       MotherBoard.USB usb = new MotherBoard.USB();
       System.out.println("Total Ports = " + usb.getTotalPorts());
   }
}

// output:
// Total Ports = 3
```



### 2.2 Accessing members of Outer class inside Static Inner Class (Accessing Members)

* **The non-static variable this cannot be referenced from a static context**

#### Error Example: (Wrong EX)

```java
class MotherBoard {
  String model;
  public MotherBoard(String model) {
    this.model = model;
  }
	
  static class USB {
    int usb2 = 2;
    int usb3 = 1;
    int getTotalPorts() {
      if (MotherBoard.this.model.equals("MSI")) {
        return 4;
      } else {
        return usb2 + usb3;
      }
    }
  }
}

public class Main {
  public static void main(String[] args) {
    MotherBoard.USB usb = new MotherBoard.USB();
    System.out.println("Total Ports = " + usb.getTotalPorts());
  }
}

// output:
// error: non-static variable this cannot be referenced from a static context
```

