# Functional Interfaces

Functional Interface **permit exactly one abstract method inside them**. These interfaces are also called **Single Abstract Method interfaces \(SAM Interfaces\)**. In Java 8, functional interfaces can be represented using lambda expressions, method reference and constructor references as well.

```java
@FunctionalInterface
public interface MyFirstFunctionalInterface 
{
    public void firstWork();
}
```

Six basic function interfaces.

| Interface | Signature | Examples |
| :--- | :--- | :--- |
| `UnaryOperator<T>` | `T apply(T t)` | `String::toLowerCase`, `Math::tan` |
| `BinaryOperator<T>` | `T apply(T t1, T t2)` | `BigInteger::add`, `Math::pow` |
| `Function<T, R>` | `R apply(T t)` | `Arrays::asList`, `Integer::toBinaryString` |
| `Predicate<T, U>` | `boolean test(T t, U u)` | `String::isEmpty`, `Character::isDigit` |
| `Supplier<T>` | `T get()` | `LocalDate::now`, `Instant::now` |
| `Consumer<T>` | `void accept(T t)` | `System.out::println`, `Error::printStackTrace` |

```java
public class Java8Function3 {

    public static void main(String[] args) {

        Java8Function3 obj = new Java8Function3();

        List<String> list = Arrays.asList("node", "c++", "java", "javascript");

        // lambda
        Map<String, Integer> map = obj.convertListToMap(list, x -> x.length());

        System.out.println(map);    // {node=4, c++=3, java=4, javascript=10}

        // method reference
        Map<String, Integer> map2 = obj.convertListToMap(list, obj::getLength);

        System.out.println(map2);
    }

    public <T, R> Map<T, R> convertListToMap(List<T> list, Function<T, R> func) {

        Map<T, R> result = new HashMap<>();
        for (T t : list) {
            result.put(t, func.apply(t));
        }
        return result;

    }

    public Integer getLength(String str) {
        return str.length();
    }

}
```

