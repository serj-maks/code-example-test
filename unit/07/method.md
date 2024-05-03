```java
public void download() throws IOException {
    try (InputStream inputStream =  client.getPage("http://example.com")) {
        File file = new File("example.html");
        copyHtmlPageToFile(inputStream, file);
    }
}
```
