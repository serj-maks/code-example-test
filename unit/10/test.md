```java
public void divide_byZero {
    Assertions.assertThrows(ArithmeticException.class, () -> Calculator.divide(10, 0));
}
```
