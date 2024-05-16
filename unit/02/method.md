```java
// source: ilya-java-mentoring-func-programming-4
public List<E> fill(Supplier<E> supplier, int elemCount) {
    ExtendedList<E> result = new ExtendedList<>();
    for (int i = 0; i < elemCount; i++) {
        result.add(supplier.get());
    }
    return result;
}
```
