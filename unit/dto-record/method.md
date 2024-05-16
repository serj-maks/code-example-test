```java
// здесь тестируется не метод, а класс
// source: ilya-java-mentoring-task-tracker-spring-10/tasktrackerspring-api/.../dto/task/TaskUpdateDto.java
public record TaskUpdateDto(@NotBlank String title,
                            LocalDate deadline,
                            Priority priority,
                            Status status,
                            String description) {
}
```
