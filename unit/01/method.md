```java
// source: ilya-java-mentoring-func-programming-4
public <R> List<R> map(Function<E, R> mapper) {
    ExtendedList<R> result = new ExtendedList<>();
    for (E elem : this) {
        R mapped = mapper.apply(elem);
        result.add(mapped);
    }
    return result;
}
```
