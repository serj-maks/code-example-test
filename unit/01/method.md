```java
public <R> List<R> map(Function<E, R> mapper) {
    ExtendedList<R> result = new ExtendedList<>();
    for (E elem : this) {
        R mapped = mapper.apply(elem);
        result.add(mapped);
    }
    return result;
}
```
