```java
// source: ilya-java-mentoring-func-programming-4
public boolean forAll(Predicate<E> predicate) {
    for (E elem : this) {
        if (!predicate.test(elem)) {
            return false;
        }
    }
    return true;
}
```
