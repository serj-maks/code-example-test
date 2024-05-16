```java
// source: ilya-java-mentoring-task-tracker-spring-10/tasktrackerspring-impl/.../exception/ArleadyExistsException.java
@ResponseStatus(code = HttpStatus.BAD_REQUEST)
public class AlreadyExistsException extends RuntimeException {

    public AlreadyExistsException(Class<?> entity, String subject) {
        super(String.format("'%s' with '%s' already exists", entity.getSimpleName(), subject));
    }
}
```
