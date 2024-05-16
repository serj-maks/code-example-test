```java
class AlreadyExistsExceptionTest {

    @Test
    void alreadyExistsException_messageCheck() {
        Project project = new Project()
            .setName("Sales")
            .setDescription("sales desc");

        AlreadyExistsException exception = assertThrows(
            AlreadyExistsException.class, () -> {
                throw new AlreadyExistsException(Project.class, "name: " + project.getName());
            }
        );

        assertEquals("'Project' with 'name: Sales' already exists", exception.getMessage());
    }
}
```
