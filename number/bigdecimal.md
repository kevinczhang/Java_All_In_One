# BigDecimal

_**BigDecimal**_ **represents an immutable arbitrary-precision signed decimal number**. It consists of two parts:

* Unscaled value – an arbitrary precision integer
* Scale – a 32-bit integer representing the number of digits to the right of the decimal point

For example, the _BigDecimal_ 3.14 has the unscaled value of 314 and the scale of 2.

**We use** _**BigDecimal**_ **for high-precision arithmetic. We also use it for calculations requiring control over scale and rounding off behavior**.  One such example is calculations involving financial transactions.

**We can create a** _**BigDecimal**_ **object from** _**String**_**, character array,** _**int**_**,** _**long**_**, and** _**BigInteger**_:  **we should use the** _**valueOf**_ **method in preference to the constructors**.

* The two java primitive types\(double and float\) are floating point numbers, which is stored as a binary representation of a fraction and a exponent.
* Other primitive types\(except boolean\) are fixed-point numbers. Unlike fixed point numbers, floating point numbers will most of the times return an answer with a small error \(around 10^-19\) This is the reason why we end up with 0.009999999999999998 as the result of 0.04-0.03 in the above example.

A `BigDecimal` is an exact way of representing numbers. A `Double` has a certain precision. Working with doubles of various magnitudes \(say `d1=1000.0` and `d2=0.001`\) could result in the `0.001` being dropped altogether when summing as the difference in magnitude is so large. With `BigDecimal` this would not happen.

The disadvantage of `BigDecimal` is that it's slower, and it's a bit more difficult to program algorithms that way \(due to `+` `-` `*` and `/` not being overloaded\).

## Operations on _BigDecimal_

 _**BigDecimal**_ **has methods to extract various attributes, such as precision, scale, and sign**_._

```java
@Test
public void whenGettingAttributes_thenExpectedResult() {
    BigDecimal bd = new BigDecimal("-12345.6789");
         
    assertEquals(9, bd.precision());
    assertEquals(4, bd.scale());
    assertEquals(-1, bd.signum());
}
```

 P**erform arithmetic operations by calling the corresponding methods**

```java
@Test
public void whenPerformingArithmetic_thenExpectedResult() {
    BigDecimal bd1 = new BigDecimal("4.0");
    BigDecimal bd2 = new BigDecimal("2.0");
 
    BigDecimal sum = bd1.add(bd2);
    BigDecimal difference = bd1.subtract(bd2);
    BigDecimal quotient = bd1.divide(bd2);
    BigDecimal product = bd1.multiply(bd2);
 
    assertTrue(sum.compareTo(new BigDecimal("6.0")) == 0);
    assertTrue(difference.compareTo(new BigDecimal("2.0")) == 0);
    assertTrue(quotient.compareTo(new BigDecimal("2.0")) == 0);
    assertTrue(product.compareTo(new BigDecimal("8.0")) == 0);
}
```

_**Equals**_ **method considers two** _**BigDecimal**_ **objects as equal only if they are equal in value and scale.**  **Since** _**BigDecimal**_ **is immutable, these operations do not modify the existing objects.** Rather, they return new objects.

## Rounding and _BigDecimal_

 **There are two classes which control rounding behavior –** _**RoundingMode**_ **and** _**MathContext**_.

The _enum_ [_RoundingMode_](https://docs.oracle.com/javase/8/docs/api/java/math/RoundingMode.html) __provides eight rounding modes:

* _CEILING –_ rounds towards positive infinity
* _FLOOR –_ rounds towards negative infinity
* _UP –_ rounds away from zero
* _DOWN –_ rounds towards zero
* _HALF\_UP –_ rounds towards “nearest neighbor” unless both neighbors are equidistant, in which case rounds up
* _HALF\_DOWN –_ rounds towards “nearest neighbor” unless both neighbors are equidistant, in which case rounds down
* _HALF\_EVEN –_ rounds towards the “nearest neighbor” unless both neighbors are equidistant, in which case, rounds towards the even neighbor
* _UNNECESSARY –_ no rounding is necessary and _ArithmeticException_ is thrown if no exact result is possible

_HALF\_EVEN_ rounding mode minimizes the bias due to rounding operations. It is frequently used. It is also known as the **banker’s rounding**.

[_**MathContext**_ ****](https://docs.oracle.com/javase/8/docs/api/java/math/MathContext.html)**encapsulates both precision and rounding mode**.  There are few predefined MathContexts:

* _DECIMAL32_ – 7 digits precision and a rounding mode of HALF\_EVEN
* _DECIMAL64_ – 16 digits precision and a rounding mode of HALF\_EVEN
* _DECIMAL128_ – 34 digits precision and a rounding mode of HALF\_EVEN
* _UNLIMITED_ – unlimited precision arithmetic

```java
@Test
public void whenRoundingDecimal_thenExpectedResult() {
    BigDecimal bd = new BigDecimal("2.5");
    // Round to 1 digit using HALF_EVEN
    BigDecimal rounded = bd
        .round(new MathContext(1, RoundingMode.HALF_EVEN));
 
    assertEquals("2", rounded.toString());
}
```

