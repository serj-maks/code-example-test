```java
@Test
void partition() {
    Map<Boolean, List<Integer>> map = new HashMap<>();
    ExtendedList<Integer> integers = new ExtendedList<>(2, 4, 6);
    List<Integer> emptyList = new ArrayList<>();
    map.put(true, integers);
    map.put(false, emptyList);
    Predicate<Integer> predicate = x -> x % 2 == 0;
    Map<Boolean, List<Integer>> expected = map;
    Map<Boolean, List<Integer>> actual = integers.partition(predicate);
    assertEquals(expected, actual);
}
```

```java
@Test
@DisplayName("should separate input list")
void partition_separateInputList() {
    // 1 - given
    ExtendedList<Integer> integers = new ExtendedList<>(1, 2, 3, 4, 5, 6, 7);
    Map<Boolean, List<Integer>> expected = new HashMap<>();
    expected.put(true, List.of(2, 4, 6));
    expected.put(false, List.of(1, 3, 5, 7));

    // 2 - when
    Predicate<Integer> predicate = x -> x % 2 == 0;
    Map<Boolean, List<Integer>> actual = integers.partition(predicate);

    // 3 - then
    assertEquals(expected, actual);
}
```
