```java
// source: ilya-java-mentoring-func-programming-4
public E reduce(BinaryOperator<E> binaryOperator, E identity) {
    E result = identity;
    for (E element : this) {
        result = binaryOperator.apply(result, element);
    }
    return result;
}
```
