# Garbage Collection

**Unreachable objects :** An object is said to be unreachable iff it doesn’t contain any reference to it. Also note that objects which are part of [island of isolation](https://www.geeksforgeeks.org/island-of-isolation-in-java/) are also unreachable. 

```java
Integer i = new Integer(4);
// the new Integer object is reachable  via the reference in 'i' 
i = null;
// the Integer object is no longer reachable. 
```

###  **Ways to make an object eligible for GC**

1. Nullifying the reference variable
2. Re-assigning the reference variable
3. Object created inside method
4. [Island of Isolation](https://www.geeksforgeeks.org/island-of-isolation-in-java/)

 **Island of Isolation:**

* Object 1 references Object 2 and Object 2 references Object 1. Neither Object 1 nor Object 2 is referenced by any other object. That’s an island of isolation.
* Basically, an island of isolation is a group of objects that reference each other but they are not referenced by any active object in the application. Strictly speaking, even a single unreferenced object is an island of isolation too.

###  **Ways for requesting** [**JVM**](https://www.geeksforgeeks.org/jvm-works-jvm-architecture/) **to run Garbage Collector**

1. **Using** _**System.gc\(\)**_ **method** : System class contain static method _gc\(\)_ for requesting JVM to run Garbage Collector.
2. **Using** _**Runtime.getRuntime\(\).gc\(\)**_ **method** : [Runtime class](https://www.geeksforgeeks.org/java-lang-runtime-class-in-java/) allows the application to interface with the JVM in which the application is running. Hence by using its gc\(\) method, we can request JVM to run Garbage Collector.

###  **Finalization**

Just before destroying an object, Garbage Collector calls _finalize\(\)_ method on the object to perform cleanup activities. Once _finalize\(\)_ method completes, Garbage Collector destroys that object.

1. The _finalize\(\)_ method called by Garbage Collector not [JVM](https://www.geeksforgeeks.org/jvm-works-jvm-architecture/). Although Garbage Collector is one of the module of JVM.
2. [Object class](https://www.geeksforgeeks.org/object-class-in-java/) _finalize\(\)_ method has empty implementation, thus it is recommended to override _finalize\(\)_method to dispose of system resources or to perform other cleanup.
3. The _finalize\(\)_ method is never invoked more than once for any given object.
4. If an uncaught exception is thrown by the _finalize\(\)_ method, the exception is ignored and finalization of that object terminates.

