---
description: Lambda expression (or function) is just an anonymous function
---

# Lambda Expression

## Overview 

The basic _syntax of a lambda expression_ is:

```text
either
(parameters) -> expression
or
(parameters) -> { statements; }
or 
() -> expression
```

 The most important features of Lambda Expressions is that **they execute in the context of their appearance**. 

## **Examples**

```java
// takes two integers and returns their multiplication
(int a, int b) ->    a * b               
// takes two numbers and returns their difference 
(a, b)          ->   a - b               
// takes no values and returns 99 
() -> 99                                
// takes a string, prints its value to the console, and returns nothing  
(String a) -> System.out.println(a)     
// takes a number and returns the result of doubling it 
a -> 2 * a                               
// takes a collection and do some procesing 
c -> { //some complex statements }   
```

####  **1\) Iterating over a List and perform some operations**

```java
List<String> pointList = new ArrayList();
pointList.add("1");
pointList.add("2");
 
pointList.forEach(p ->  {
                            System.out.println(p);
                            //Do more work
                        }
                 );
```

 **2\) Create a new runnable and pass it to thread**

```java
new Thread(
    () -> System.out.println("My Runnable"); 
).start();
```

 **3\) Sorting employees objects by their name**

```java
public class LambdaIntroduction {
 
  public static void main (String[] ar){
          Employee[] employees  = {
              new Employee("David"),
              new Employee("Naveen"),
              new Employee("Alex"),
              new Employee("Richard")};
            
          System.out.println("Before Sorting Names: "+Arrays.toString(employees));
          Arrays.sort(employees, Employee::nameCompare);
          System.out.println("After Sorting Names "+Arrays.toString(employees));
      }
}
  
class Employee {
  String name;
  
  Employee(String name) {
    this.name = name;
  }
  
  public static int nameCompare(Employee a1, Employee a2) {
    return a1.name.compareTo(a2.name);
  }
    
  public String toString() {
    return name;
  }
}
 
Output:
 
Before Sorting Names: [David, Naveen, Alex, Richard]
After Sorting Names [Alex, David, Naveen, Richard]
```

 **4\) Adding an event listener to a GUI component**

```java
JButton button =  new JButton("Submit");
button.addActionListener((e) -> {
    System.out.println("Click event triggered !!");
}); 
```

