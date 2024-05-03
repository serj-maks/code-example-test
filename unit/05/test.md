```java
@Test
void reduce_additionOperation() {
    ExtendedList<Integer> integers = new ExtendedList<>(2,2,3);
    Integer expected = 7;
    BinaryOperator<Integer> addition = (a, b) -> a + b;
    Integer actual = integers.reduce(addition, 0);
    assertEquals(expected, actual);
}
```

```java
@Test
void reduce_multiplyOperation(){
    ExtendedList<Integer> integers = new ExtendedList<>(2,2,3);
    Integer expected = 12;
    BinaryOperator<Integer> multiply = (a, b) -> a * b;
    Integer actual = integers.reduce(multiply, 1);
    assertEquals(expected, actual);
}
```

```java
@Test
void reduce_MultiplyOperationShouldEqualsNull(){
    ExtendedList<Integer> integers = new ExtendedList<>(2,2,3);
    Integer expected = 0;
    BinaryOperator<Integer> multiply = (a, b) -> a * b;
    Integer actual = integers.reduce(multiply, 0);
    assertEquals(expected, actual);
}
```
