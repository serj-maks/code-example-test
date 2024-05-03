```java
@Test
void fill() {
    ExtendedList<Integer> integers = new ExtendedList<>();
    ExtendedList<Integer> expected = new ExtendedList<>(1,2,3,4,5);
    Supplier<Integer> supplier = () -> (int) (Math.random() * 100);
    List<Integer> actual = integers.fill(supplier, 5);
    int expectedSize = expected.size();
    int actualSize = actual.size();
    assertEquals(expectedSize, actualSize);
}
```
