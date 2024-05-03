```java
public class ClientMock implements Client {

    @Override
    public InputStream getPage(String link) throws IOException {
        // return new ByteArrayInputStream(new byte[] {1});
        return new ByteArrayInputStream("str".getBytes());
    }
}
```

```java
@AfterEach
void tearDown() throws IOException {
    Files.deleteIfExists(Path.of("example.html"));
}

@Test
void download() throws IOException {
    PageDownloader pd = new PageDownloader(new ClientMock());
    pd.download();
    byte[] result = Files.readAllBytes(Path.of("example.html"));
    String actual = new String(result);
    String expected = "str";
    assertEquals(expected, actual);
}
```
