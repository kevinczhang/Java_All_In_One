# Default Methods

Java 8 allows you to add non-abstract methods in interfaces. These methods must be declared default methods.

```java
public interface Moveable {
    default void move(){
        System.out.println("I am moving");
    }
}
```

And if class willingly wants to customize the behavior then it can provide it’s own custom implementation and override the method.

```java
public class Animal implements Moveable{
     
    public void move(){
        System.out.println("I am running");
    }
     
    public static void main(String[] args){
        Animal tiger = new Animal();
        tiger.move();
    }
}
 
Output: I am running
```

This is not all done here. Best part comes as following benefits:

1. Static default methods: You can define static default methods in interface which will be available to all instances of class which implement this interface. This makes it easier for you to organize helper methods in your libraries; you can keep static methods specific to an interface in the same interface rather than in a separate class. This enables you to define methods out of your class and yet share with all child classes.
2. They provide you an highly desired capability of adding a capability to number of classes without even touching their code. Simply add a default method in interface which they all implement.

### Why default methods were needed in java 8?

**Simplest answer is to enable the functionality of lambda expression in java.** Lambda expression are essentially of type of functional interface. 

### **Rules for this conflict resolution are as follows:**

**1\)** Most preferred are the overridden methods in classes. They will be matched and called if found before matching anything.  
**2\)** The method with the same signature in the “most specific default-providing interface” is selected. This means if class Animal implements two interfaces i.e. Moveable and Walkable such that Walkable extends Moveable. Then Walkable is here most specific interface and default method will be chosen from here if method signature is matched.  
**3\)** If Moveable and Walkable are independent interfaces then a serious conflict condition happen, and compiler will complain then it is unable to decide. The you have to help compiler by providing extra info that from which interface the default method should be called. e.g.

