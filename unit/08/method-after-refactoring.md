```java
private final File FILE = new File("src/main/resources/files_for_comparing");

// after refactoring
public String findMaxS() {
    Map<String, Integer> fileMap = new HashMap<>();
    File[] filesArray = FILE.listFiles();
    for (File file : filesArray) {
        if (!file.isDirectory()) {
            String filePath = file.getPath();
            int totalCharacters = countS(file.getName());
            fileMap.put(filePath, totalCharacters);
        }
    }
    return Collections.max(fileMap.entrySet(), Comparator.comparingInt(Map.Entry::getValue)).getKey();
}

private int countS(String fileName) {
    int totalCharacters = 0;
    for (int i = 0; i < fileName.length(); i++) {
        if (fileName.charAt(i) == 's') {
            totalCharacters++;
        }
    }
    return totalCharacters;
}
```
