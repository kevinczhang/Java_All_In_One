---
description: >-
  BigInteger represents immutable arbitrary-precision integers. It is similar to
  the primitive integer types but allows arbitrary large values.
---

# BigInteger

**It is used when integers involved are larger than the limit of** _**long**_ **type.** It is widely used in security and cryptography applications.

_**BigInteger**_ **can be created from a** _**byte**_ **array or** _**String or**_ **by converting a** _**long**_ **to** _**BigInteger**_ **using the static method** _**valueOf.**_

```java
BigInteger biFromString = new BigInteger("1234567890987654321");
BigInteger biFromByteArray = new BigInteger(new byte[] { 64, 64, 64, 64, 64, 64 });
BigInteger biFromSignMagnitude = new BigInteger(-1, new byte[] { 64, 64, 64, 64, 64, 64 });
BigInteger bi =  BigInteger.valueOf(2305843009213693951L);
```

## Operations on _BigInteger_

 _BigInteger_ implements all the arithmetic and logical operations. But, it does not overload the operators.  As _BigInteger_ is immutable, **these operations do not modify the existing objects.** Unlike, _int_ and _long_, **these operations do not overflow.**

```java
BigInteger i = new BigInteger("4");
BigInteger j = new BigInteger("2");
 
BigInteger sum = i.add(j);
BigInteger difference = i.subtract(j);
BigInteger quotient = i.divide(j);
BigInteger product = i.multiply(j);

assertTrue(i.compareTo(i) == 0);
assertTrue(j.compareTo(i) < 0);
```

## Bit operations

```java
@Test
public void givenBigIntegers_whenPerformingBitOperations_thenExpectedResult() {
    BigInteger i = new BigInteger("17");
    BigInteger j = new BigInteger("7");
 
    BigInteger and = i.and(j);
    BigInteger or = i.or(j);
    BigInteger not = j.not();
    BigInteger xor = i.xor(j);
    BigInteger andNot = i.andNot(j);
    BigInteger shiftLeft = i.shiftLeft(1);
    BigInteger shiftRight = i.shiftRight(1);
 
    assertEquals(new BigInteger("1"), and);
    assertEquals(new BigInteger("23"), or);
    assertEquals(new BigInteger("-8"), not);
    assertEquals(new BigInteger("22"), xor);
    assertEquals(new BigInteger("16"), andNot);
    assertEquals(new BigInteger("34"), shiftLeft);
    assertEquals(new BigInteger("8"), shiftRight);
}

@Test
public void givenBigIntegers_whenPerformingBitManipulations_thenExpectedResult() {
    BigInteger i = new BigInteger("1018");
 
    int bitCount = i.bitCount();
    int bitLength = i.bitLength();
    int getLowestSetBit = i.getLowestSetBit();
    boolean testBit3 = i.testBit(3);
    BigInteger setBit12 = i.setBit(12);
    BigInteger flipBit0 = i.flipBit(0);
    BigInteger clearBit3 = i.clearBit(3);
 
    assertEquals(8, bitCount);
    assertEquals(10, bitLength);
    assertEquals(1, getLowestSetBit);
    assertEquals(true, testBit3);
    assertEquals(new BigInteger("5114"), setBit12);
    assertEquals(new BigInteger("1019"), flipBit0);
    assertEquals(new BigInteger("1010"), clearBit3);
}
```

