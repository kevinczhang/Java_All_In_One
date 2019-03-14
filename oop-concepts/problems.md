# Problems

## Immutable class

The below class is immutable because: 

* The instance variable of the class is final i.e. we cannot change the value of it after creating an object. 
* The class is final so we cannot create the subclass. 
* There is no setter methods i.e. we have no option to change the value of the instance variable. These points makes this class as immutable.

```java
public final class Employee {
      final String pancardNumber;  
      public Employee(String pancardNumber) {
           this.pancardNumber=pancardNumber;  
      }  
      public String getPancardNumber(){  
           return pancardNumber;  
      }  
}
```



