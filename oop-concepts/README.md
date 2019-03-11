---
description: >-
  The term Object-Oriented explains the concept of organizing the software as a
  combination of different types of objects that incorporates both data and
  behavior.
---

# OOP concepts

## Classes and Objects

### Classes

 A class is a user defined blueprint or prototype from which objects are created.  It represents the set of properties or methods that are common to all objects of one type.

In general, class declarations can include these components, in order:

1. **Modifiers** : A class can be public or has default access.
2. **Class name:** The name should begin with a initial letter \(capitalized by convention\).
3. **Superclass\(if any\):** The name of the class’s parent \(superclass\), if any, preceded by the keyword extends. A class can only extend \(subclass\) one parent.
4. **Interfaces\(if any\):** A comma-separated list of interfaces implemented by the class, if any, preceded by the keyword implements. A class can implement more than one interface.
5. **Body:** The class body surrounded by braces, { }.

The classes and interfaces themselves can have only two access specifiers when declared outside any other class.  
1\) public  
2\) default \(when no access specifier is specified\)

We cannot declare class/interface with private or protected access specifiers.

### Objects

 It is a basic unit of Object Oriented Programming and represents the real life entities.

## Encapsulation

It is the mechanism that binds together code and the data it manipulates.  Other way to think about encapsulation is, it is a protective shield that prevents the data from being accessed by the code outside this shield.

## Inheritance

 It is the mechanism in java by which one class is allow to inherit the features\(fields and methods\) of another class.  The keyword used for inheritance is **extends**.

```java
class derived-class extends base-class  
{  
   //methods and fields  
}
```

## Abstraction

 Data Abstraction may also be defined as the process of identifying only the required characteristics of an object ignoring the irrelevant details.

 In java, abstraction is achieved by [interfaces](https://www.geeksforgeeks.org/interfaces-in-java/) and [abstract classes](https://www.geeksforgeeks.org/abstract-classes-in-java/). We can achieve 100% abstraction using interfaces.

**Abstract class vs Interface**

1. **Type of methods:** Interface can have only abstract methods. Abstract class can have abstract and non-abstract methods. From Java 8, it can have default and static methods also.
2. **Final Variables:** Variables declared in a Java interface are by default final. An abstract class may contain non-final variables.
3. **Type of variables:** Abstract class can have final, non-final, static and non-static variables. Interface has only static and final variables.
4. **Implementation:** Abstract class can provide the implementation of interface. Interface can’t provide the implementation of abstract class.
5. **Inheritance vs Abstraction:** A Java interface can be implemented using keyword “implements” and abstract class can be extended using keyword “extends”.
6. **Multiple implementation:** An interface can extend another Java interface only, an abstract class can extend another Java class and implement multiple Java interfaces.
7. **Accessibility of Data Members:** Members of a Java interface are public by default. A Java abstract class can have class members like private, protected, etc.

##  Polymorphism

 **Polymorphism in Java** is a concept by which we can perform a _single action in different ways_.  

There are two types of polymorphism in Java: compile-time polymorphism and runtime polymorphism. We can perform polymorphism in java by method overloading and method overriding.

