<center> 
<h1>Data Structures & Algorithms for Beginners - 1</h1> 
<h2></h2>
</center>


---

## A. Big O Notation

Use Big O Notation to describe the performance of an algorithm

### 1. **O(n)** /Linear/

```java
public class Main {
  public void log(int[] numbers) {
    // O(1)
    System.out.println(numbers[0]);
    System.out.println(numbers[0]);
  }
}
```

```java
public class Main {
  public void log(int[] numbers) {
    // O(2 + n) ==> O(n)
    System.out.println(); // O(1)
    // for (int i = 0; i < numbers.length; i++)
    for (int number : numbers) { // O(n)
    	System.out.println(number);
    }
    System.out.println(); // O(1)
  }
}
```

```java
public class Main {
	public void log(int[] numbers) {
    // O(2n) ==> O(n)
    for (int number : numbers) { // O(n)
    	System.out.println(number);
    }
    
    for (int number : numbers) { // O(n)
    	System.out.println(number);
    }
  }
}

```

```java
public class Main {
	public void log(int[] numbers, String[] names) {
    // O(n + m) ==> O(n)
    for (int number : numbers) { // O(n)
    	System.out.println(number);
    }
    
    for (int name : names) { // O(m)
    	System.out.println(name);
    }
  }
}
```



### 2. **O(n^2)** /Quadratic/

```java
public class Main {
	public void log(int[] numbers) {
    // O(n * n) ==> O(n^2)
    for (int first : numbers) { // O(n)
      for (int second : numbers) { // O(n)
        System.out.println(first + ", " + second);
      }
    }
  }
}
```

```java
public class Main {
	public void log(int[] numbers) {
    // O(n + n^2) ==> O(n^2)
   	for (int number : numbers) { // O(n)
    	System.out.println(number);
    }
    
    for (int first : numbers) { // O(n)
      for (int second : numbers) { // O(n)
        System.out.println(first + ", " + second);
      }
    }
  }
}
```

```java
public class Main {
	public void log(int[] numbers) {
    // O(n * n * n) ==> O(n^3)
    for (int first : numbers) { // O(n)
      for (int second : numbers) { // O(n)
        for (int third : numbers) { // O(n)
          System.out.println(first + ", " + second + ", " + third);
        }
      }
    }
  }
}
```



### 3. **O(log n) ** /Logarithmic/

Example: Binary Search

```java
class BinarySearch {
    int binarySearch(int arr[], int l, int r, int x) {
        if (r >= l) {
            int mid = l + (r - l) / 2;
            if (arr[mid] == x)
                return mid;
        
            if (arr[mid] > x)
                return binarySearch(arr, l, mid - 1, x);
            return binarySearch(arr, mid + 1, r, x);
        }
        return -1;
    }

    public static void main(String args[]) {
        BinarySearch ob = new BinarySearch();
        int arr[] = { 2, 3, 4, 10, 40 };
        int n = arr.length;
        int x = 10;
        int result = ob.binarySearch(arr, 0, n - 1, x);
        if (result == -1)
            System.out.println("Element not present");
        else
            System.out.println("Element found at index " + result);
    }
}
```



### 4. O(2^n) /Exponential/





### 5. O(x)

```java
public class Main {
	public void greet(String[] names) {
    // O(n) space
    String[] copy = new String[names.length];
    
    for (int i = 0; i < names.length; i++) {
    	System.out.println("Hi " + names[i]);
    }
  }
}
```



## B. Arrays

Lookup O(1)

Insert O(n)

Delete O(n)

```java
import java.util.Arrays;

public class Main {
	public void main(String[] args) {
    int[] numbers = new int[3];
    numbers[0] = 10;
    numbers[1] = 20;
    numbers[2] = 30;
    System.out.println(Arrys.toString(numbers));
  }
}
```



### Exercise: Build a Dynamic Array from Strach

Array.java (insert, remove, print)

```java
public class Array {
  public Array(int length) {
    private int[] items;
    private int count;
    
    public Array(int length) {
      if (items.length == count) {
        int[] newItem = new int[count * 2];
        for (int i = 0; i < count; i++) {
          newItems[i] = items[i];
        }
        items = newItems;
      }
      items = new int[length];
    }
    
    public void insert(int item) {
      items[count++] = item;
    }
    
    public void removeAt(int index) {
      if (index < 0 || index >= count) {
        throw new IllegalArgumentException();
      }
      for (int i = index; i < count; i++) {
        items[i] = items[i + 1];
      }
      count--;
    }
    
    public int indexOf(int item) {
      // O(n)
      for (int i = 0; i < count; i++) {
        if (items[i] == item) {
          return i;
        } 
      }
      return -1;
    }
    
    public void print() {
      for (int i = 0; i < count; i++) {
        System.out.println(items[i]);
      }
    }
    
  }
}
```

Main.java

```java
public class Main {
	public static void main(String[] args) {
    Array numbers = new Array(3);
    numbers.insert(10);
    numbers.insert(20);
    numbers.insert(30);
    numbers.insert(40);
    System.out.println(numbers.indexOf(10));
    numbers.print();
    numbers.removeAt(1);
    numbers.print();
  }
}
```



## C. Dynamic Array

```java
import java.util.ArrayList;

public class Main {
  public static void main(String[] args) {
    // Vector: 100% - synchronized
    // ArrayList: 50% (use this in here)
    ArrayList<Integer> list = new ArrayList<>();
    list.add(10);
    list.add(20);
    list.add(30);
    list.remove(0);
    list.indexOf(20);
    list.lastIndexOf(20);
    list.size();
    list.toArray();
    System.out.println(list);
  }
}
```





## D. Linked Lists

| Lookup        | Insert                | Delete                  |
| ------------- | --------------------- | ----------------------- |
| By Value O(n) | At the End O(1)       | From the Beginning O(1) |
| By Index O(n) | At the Beginning O(1) | From the End O(n)       |
|               | In the Middle o(n)    | From the Middle O(n)    |



```java
import java.util.LinkedList

public class Main {
  public static void main(String[] args) {
    LinkedList<Integer> list = new LinkedList();
    list.addLast(10);
    list.addLast(20);
    list.addLast(30);
    list.addFirst(5);
    list.removeFirst();
    list.removeLast();
    
    System.out.println(list.contains(10)); // true
    System.out.println(list.indexOf(10)); // 0
    System.out.println(list.size());
    var array = list.toArray();
    System.out.println(Arrays.toString(array));
  }
}
```



### Exercise: Build a Linked List from Strach

Main.java

```java
public class Main {
  public static void main(String[] args) {
    var list = new LinkedList();
    list.addLast(10);
    list.addLast(20);
    list.addLast(30);
    list.removeFirst();
    list.removeLast();
    System.out.println(list.indexOf(10));
    System.out.println(list.contains(10));
  }
}
```

LinkedList.java (Add Last + Add First + IndexOf + Contains + Remove First + Remove Last)

```java
public class LinkedList {
  private class Node {
  	private int value;
  	private Node next;
    
    public void setValue(int value) {
    	this.value = value;
  	}
 	}
  
  private Node first;
  private Node last;
  
  public void addLast(int item) {
    var node = new Node(item);
    
    if (isEmpty()) {
      first = last = node;
    } else {
      last.next = node;
      last = node;
    }
  }
  
  public void addFirst(int item) {
    var node = new Node(item);
    
    if (isEmpty()) {
      first = last = node;
    } else {
      node.next = first;
      first = node;
    }
  }
  
  private boolean isEmpty() {
    return first == null;
  }
  
  public int indexOf(int item) {
    int index = 0;
    var current = first;
    while (current != null) {
      if (current.value == item) {
        return index;
      }
      current = curreny.next;
      index++;
    }
    return -1;
  }
  
  public boolean contains(int item) {
    return indexOf(item) != -1;
  }
  
  public void removeFirst() {
    if (isEmpty()) {
      throw new NoSuchElementException();
    }
    if (first == last) {
      first = last = null;
      return;
    }
    var second = first.next;
    first.next = null;
    first = second;
  }
  
  public void removeLast() {
    if (isEmpty()) {
      throw new NoSuchElementException();
    }
    if (first == last) {
      first = last = null;
      return;
    }
    var previous = getPrevious(last);
    last = previous;
    last.next = null;
  }
  
  private Node getPrevious(Node node) {
    var current = first;
    while (current != null) {
      if (current.next == last) {
        return current;
      } else {
        current = current.next;
      }
    }
    return null;
  }
}
```











































