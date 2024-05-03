```java
public Map<Boolean, List<E>> partition(Predicate<E> predicate) {
    List<E> listTrue = new ArrayList<>();
    List<E> listFalse = new ArrayList<>();
    for (E elem : this) {
        if (predicate.test(elem)) {
            listTrue.add(elem);
        } else {
            listFalse.add(elem);
        }
    }
    Map<Boolean, List<E>> result = new HashMap<>();
    result.put(true, listTrue);
    result.put(false, listFalse);
    return result;
}
```
