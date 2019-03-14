# Overview

## Run time environment

Java is a general-purpose computer programming language that is concurrent, class-based, object-oriented etc.  
Java applications are typically compiled to **bytecode** that can run on any Java virtual machine \(JVM\) regardless of computer architecture.The latest version is **Java 11**. 

JVM, JRE and JDK  all three are platform dependent because configuration of each Operating System is different. But, Java is platform independent.

1. **JDK**\(Java Development Kit\) : JDK is intended for software developers and includes development tools such as the Java compiler, Javadoc, Jar, and a debugger.
2. **JRE**\(Java Runtime Environment\) : JRE contains the parts of the Java libraries required to run Java programs and is intended for end users. JRE can be view as a subset of JDK.
3. **JVM:** JVM \(Java Virtual Machine\) is an abstract machine. It is a specification that provides runtime environment in which java bytecode can be executed. JVMs are available for many hardware and software platforms. 

## Steps to run Java code

The process of Java programming can be simplified in three steps:

* Create the program by typing it into a text editor and saving it to a file – HelloWorld.java.
* Compile it by typing “javac HelloWorld.java” in the terminal window.
* Execute \(or run\) it by typing “java HelloWorld” in the terminal window.

## Class loading

 **Note :** JVM follow Delegation-Hierarchy principle to load classes. System class loader delegate load request to extension class loader and extension class loader delegate request to boot-strap class loader. If class found in boot-strap path, class is loaded otherwise request again transfers to extension class loader and then to system class loader. At last if system class loader fails to load class, then we get run-time exception _java.lang.ClassNotFoundException_.

## **JVM Memory**

 **Method area :**In method area, all class level information like class name, immediate parent class name, methods and variables information etc. are stored, including static variables. There is only one method area per JVM, and it is a shared resource.

 **Heap area :**Information of all objects is stored in heap area. There is also one Heap Area per JVM. It is also a shared resource.

 **Stack area :**For every thread, JVM create one run-time stack which is stored here. Every block of this stack is called activation record/stack frame which store methods calls. All local variables of that method are stored in their corresponding frame. After a thread terminate, it’s run-time stack will be destroyed by JVM. It is not a shared resource.

**PC Registers :**Store address of current execution instruction of a thread. Obviously each thread has separate PC Registers.

**Native method stacks :**For every thread, separate native stack is created. It stores native method information.

## JVM Stack Area

 For every thread, JVM creates a separate stack at the time of thread creation. The JVM only performs two operations directly on Java Stacks: it pushes and pops frames. After completing a method, corresponding entry from the stack is removed. After completing all method calls the stack becomes empty and that empty stack is destroyed by the JVM just before terminating the thread. 

And stack for a particular thread may be termed as **Run – Time Stack**. Each and every method call performed by that thread is stored in the corresponding run time stack including parameters, local variables, intermediate computations, and other data. 

The data stored in the stack is available for the corresponding thread and not available to the remaining threads. Hence we can say local data is thread safe. Each entry in the stack is called **Stack Frame** or **Activation Record**.

![](../.gitbook/assets/image%20%281%29.png)

![](../.gitbook/assets/image%20%289%29.png)

