```java
@Test
public void findMaxSFilename_shouldReturnTrue() {
    FindMaxSAfter findMaxS = new FindMaxSAfter();
    String actual = findMaxS.findMaxS();
    String expected = "files_for_comparing\\dssss.txt";
    assertEquals(expected, actual);
}
```
