```java
// source: ilya-java-mentoring/.../task1/tested_solution/PageDownloader.java
public void download() throws IOException {
    try (InputStream inputStream =  client.getPage("http://example.com")) {
        File file = new File("example.html");
        copyHtmlPageToFile(inputStream, file);
    }
}
```
