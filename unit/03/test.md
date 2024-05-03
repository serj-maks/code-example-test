```java
@Test
@DisplayName("should return true, if all elements is even")
void forAll_shouldReturnTrue() {
    ExtendedList<Integer> integers = new ExtendedList<>(2, 4, 6);
    Predicate<Integer> predicate = x -> x % 2 == 0;
    boolean actual = integers.forAll(predicate);
    assertTrue(actual);
}
```

```java
@Test
@DisplayName("should return false")
void forAll_shouldReturnFalse() {
    ExtendedList<Integer> integers = new ExtendedList<>(2, 3, 6);
    Predicate<Integer> predicate = x -> x % 2 == 0;
    boolean actual = integers.forAll(predicate);
    assertFalse(actual);
}
```
