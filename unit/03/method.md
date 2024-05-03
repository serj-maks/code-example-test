```java
public boolean forAll(Predicate<E> predicate) {
    for (E elem : this) {
        if (!predicate.test(elem)) {
            return false;
        }
    }
    return true;
}
```
