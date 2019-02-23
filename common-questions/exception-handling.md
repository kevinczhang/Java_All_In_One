---
description: >-
  Exception Handling is a mechanism to handle runtime errors such as
  ClassNotFound, IO, SQL, Remote etc.
---

# Exception Handling

## Overview

The core advantage of exception handling is to maintain the normal flow of the application. Exception normally disrupts the normal flow of the application that is why we use exception handling.

![Hierarchy of Java Exception classes](../.gitbook/assets/image%20%282%29.png)

## Types of Exception

There are mainly two types of exceptions: checked and unchecked where error is considered as unchecked exception. 

There are three types of exceptions: Checked Exception, Unchecked Exception and Error

### Difference between checked and unchecked exceptions 

1. Checked Exception The classes that extend Throwable class except RuntimeException and Error are known as checked exceptions e.g. IOException, SQLException etc. Checked exceptions are checked at compile-time.
2. Unchecked Exception The classes that extend RuntimeException are known as unchecked exceptions e.g. ArithmeticException, NullPointerException, ArrayIndexOutOfBoundsException etc. Unchecked exceptions are not checked at compile-time rather they are checked at runtime.
3. Error Error is irrecoverable e.g. OutOfMemoryError, VirtualMachineError, AssertionError etc.

## Difference between throw and throws

| throw | throws |
| :--- | :--- |
| Java throw keyword is used to explicitly throw an exception. | Java throws keyword is used to declare an exception. |
| Checked exception cannot be propagated using throw only. | Checked exception can be propagated with throws. |
| Throw is followed by an instance. | Throws is followed by class. |
| Throw is used within the method. | Throws is used with the method signature. |
| You cannot throw multiple exceptions. | You can declare multiple exceptions. |



