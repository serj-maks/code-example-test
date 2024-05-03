```java
private final ByteArrayOutputStream outContent = new ByteArrayOutputStream();
private final PrintStream out = System.out;

@BeforeEach
public void setUpStreams() {
    System.setOut(new PrintStream(outContent));
}

@AfterEach
public void restoreStreams() {
    System.setOut(out);
}

@Test
// integration test
// read output from console
public void execute_shouldReturnTrue() throws IOException {
    FindMaxSBefore findMaxS = new FindMaxSBefore();
    findMaxS.findMaxS();
    String expected = "files_for_comparing\\dssss.txt\r\n";
    String actual = outContent.toString();
    assertEquals(expected, actual);
}
```
