---
description: Common APIs likely to be used on whiteboard
---

# Common APIs

## ASCII Codes

1. Basic: 128, +extend: 256
2. 0 -&gt; null, 32 -&gt; Space, \(48 ~ 57\) -&gt; \(0 - 9\), 64 -&gt; @, \(65 ~ 90\) -&gt; \(A - Z\), \(97 ~ 122\) -&gt; \(a - z\)

## Math methods

All following methods are static methods

1. [`E`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#E)The `double` value that is closer than any other to e, the base of the natural logarithms.
2. [`PI`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#PI)The `double` value that is closer than any other to pi, the ratio of the circumference of a circle to its diameter. 
3. [`abs`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#abs-double-)`(double a);`Returns the absolute value of a `double` value.
4. [`cbrt`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#cbrt-double-)`(double a)`Returns the cube root of a `double` value.
5. [`ceil`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#ceil-double-)`(double a)`Returns the smallest \(closest to negative infinity\) `double` value that is greater than or equal to the argument and is equal to a mathematical integer.
6. [`exp`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#exp-double-)`(double a)`Returns Euler's number e raised to the power of a `double` value.
7. [`floor`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#floor-double-)`(double a)`Returns the largest \(closest to positive infinity\) `double` value that is less than or equal to the argument and is equal to a mathematical integer.
8. [`log`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#log-double-)`(double a)`Returns the natural logarithm \(base e\) of a `double` value.
9. [`log10`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#log10-double-)`(double a)`Returns the base 10 logarithm of a `double` value.
10. [`max`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#max-double-double-)`(double a, double b)`Returns the greater of two `double` values.
11. [`min`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#min-double-double-)`(double a, double b)`Returns the smaller of two `double` values.
12. [`pow`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#pow-double-double-)`(double a, double b)`Returns the value of the first argument raised to the power of the second argument.
13. [`random`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#random--)`()`Returns a `double` value with a positive sign, greater than or equal to `0.0` and less than `1.0`.
14. [`sqrt`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#sqrt-double-)`(double a)`Returns the correctly rounded positive square root of a `double` value.
15. [`toRadians`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#toRadians-double-)`(double angdeg)`Converts an angle measured in degrees to an approximately equivalent angle measured in radians.
16. [`toDegrees`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#toDegrees-double-)`(double angrad)`Converts an angle measured in radians to an approximately equivalent angle measured in degrees.

## Integer methods

1. [`MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#MAX_VALUE)A constant holding the maximum value an `int` can have, 231-1.
2. [`MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#MIN_VALUE)A constant holding the minimum value an `int` can have, -231.
3. [`BYTES`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#BYTES)The number of bytes used to represent a `int` value in two's complement binary form. It is 4.
4. [`SIZE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#SIZE)The number of bits used to represent an `int` value in two's complement binary form. It is 32.
5. [`parseInt`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#parseInt-java.lang.String-)`(`[`String`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) `s)`Parses the string argument as a signed decimal integer.
6. [`toBinaryString`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#toBinaryString-int-)`(int i)`Returns a string representation of the integer argument as an unsigned integer in base 2.

## Arrays methods

1. [`asList`](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#asList-T...-)`(T... a)`Returns a fixed-size list backed by the specified array.
2. [`copyOf`](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#copyOf-T:A-int-)`(T[] original, int newLength)`Copies the specified array, truncating or padding with nulls \(if necessary\) so the copy has the specified length.
3. [`copyOfRange`](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#copyOfRange-T:A-int-int-)`(T[] original, int from, int to)`Copies the specified range of the specified array into a new array.
4. [`equals`](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#equals-java.lang.Object:A-java.lang.Object:A-)`(`[`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html)`[] a,` [`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html)`[] a2)`Returns true if the two specified arrays of Objects are equal to one another.
5. [`fill`](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#fill-java.lang.Object:A-java.lang.Object-)`(`[`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html)`[] a,` [`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html) `val)`Assigns the specified Object reference to each element of the specified array of Objects.
6. [`sort`](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#sort-java.lang.Object:A-)`(`[`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html)`[] a)`Sorts the specified array of objects into ascending order, according to the [natural ordering](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html) of its elements.
7. [`sort`](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#sort-java.lang.Object:A-int-int-)`(`[`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html)`[] a, int fromIndex, int toIndex)`Sorts the specified range of the specified array of objects into ascending order, according to the [natural ordering](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html) of its elements.
8. [`sort`](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#sort-T:A-java.util.Comparator-)`(T[] a,` [`Comparator`](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html)`<? super T> c)`Sorts the specified array of objects according to the order induced by the specified comparator.
9. [`sort`](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#sort-T:A-int-int-java.util.Comparator-)`(T[] a, int fromIndex, int toIndex,` [`Comparator`](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html)`<? super T> c)`Sorts the specified range of the specified array of objects according to the order induced by the specified comparator.

