---
description: Commonly used APIs for Strings
---

# String

```java
String str = "test";
int strLen = testStr.length();
boolean strCompare = "".equals(testStr);
boolean strCompare2 = "abc".equalsIgnoreCase(testStr);
String trimedStr = testStr.trim();
boolean strStartWith = testStr.startsWith("a");
boolean strEndWith = testStr.endsWith("b");
String lowerCaseStr = testStr.toLowerCase();
String upperCaseStr = testStr.toUpperCase();
String covertToString = String.valueOf(1234);
// char in str
char[] strChars = testStr.toCharArray();
char strChar = testStr.charAt(0);
Character.isDigit(strChar);
Character.isLetter(strChar);
Character.isLetterOrDigit(strChar);
Character.isLowerCase(strChar);
Character.isUpperCase(strChar);
Character.isWhitespace(strChar);
Character.toLowerCase(strChar);
Character.toUpperCase(strChar);
```

## Compares two strings lexicographically:

1. The value 0 if the argument string is equal tothis string; 
2. A value less than 0 if this string is lexicographically less than the string argument;
3. A value greater than 0 if this string is lexicographically greater than the string argument.

```java
int StrCompareTo = "".compareTo(testStr);
```

## Replace and split methods

1.  [`replace`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#replace-char-char-)`(char oldChar, char newChar);`Returns a string resulting from replacing all occurrences of `oldChar` in this string with `newChar`.
2.  [`replaceAll`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#replaceAll-java.lang.String-java.lang.String-)`(`[`String`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) `regex,` [`String`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) `replacement);`Replaces each substring of this string that matches the given [regular expression](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html#sum) with the given replacement.
3.  [`replaceFirst`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#replaceFirst-java.lang.String-java.lang.String-)`(`[`String`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) `regex,` [`String`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) `replacement);`Replaces the first substring of this string that matches the given [regular expression](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html#sum) with the given replacement.
4.  [`split`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#split-java.lang.String-)`(`[`String`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) `regex);`Splits this string around matches of the given [regular expression](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html#sum).
5.  [`matches`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#matches-java.lang.String-)`(`[`String`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) `regex);`Tells whether or not this string matches the given [regular expression](https://docs.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html#sum).

```java
// Split on comma or colon.
String[] parts = testStr.split("[,:]");
// Split on 1+ non-word characters.
String[] words1 = testStr.split("\\W+");
// Separate based on number delimiters.
String[] words2 = testStr.split("\\d+");
// Separate by spaces or , with spaces or . With spaces
String str = "a d, m, i.n";
String delimiters = "\\s+|,\\s*|\\.\\s*";
String[] tokensVal = str.split(delimiters);
// Remove '(' or ')'
String temp = testStr.replaceAll("[()]", "");
// Join strings together
String joinedStr1 = String.join(",", splitedStr);
String joinedStr2 = String.join(",", "test1", "test2");
```

## StringBuilder methods

1.  [`append`](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#append-boolean-)`(obj b);`Appends the string representation of the `object` argument to the sequence.
2.  [`charAt`](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#charAt-int-)`(int index);`Returns the `char` value in this sequence at the specified index.
3.  [`delete`](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#delete-int-int-)`(int start, int end);`Removes the characters in a substring of this sequence
4.  [`deleteCharAt`](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#deleteCharAt-int-)`(int index);`Removes the `char` at the specified position in this sequence.
5.  [`insert`](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#insert-int-java.lang.Object-)`(int offset,` [`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html) `obj);`Inserts the string representation of the `Object` argument into this character sequence.
6.  [`length`](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#length--)`();`Returns the length \(character count\).
7.  [`replace`](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#replace-int-int-java.lang.String-)`(int start, int end,` [`String`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) `str)`Replaces the characters in a substring of this sequence with characters in the specified `String`.
8.  [`reverse`](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#reverse--)`()`Causes this character sequence to be replaced by the reverse of the sequence.
9.  [`setCharAt`](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#setCharAt-int-char-)`(int index, char ch)`The character at the specified index is set to `ch`.
10.  [`substring`](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#substring-int-)`(int start)`Returns a new `String` that contains a subsequence of characters currently contained in this character sequence.
11.  [`substring`](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#substring-int-int-)`(int start, int end)`Returns a new `String` that contains a subsequence of characters currently contained in this sequence.
12.  [`toString`](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html#toString--)`()`Returns a string representing the data in this sequence.

