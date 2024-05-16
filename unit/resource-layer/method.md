```java
// source: ilya-java-mentoring-task-tracker-spring-10/tasktrackerspring-impl/.../resource/TaskResourceImpl.java
@Slf4j
@RestController
@RequiredArgsConstructor
public class TaskResourceImpl implements TaskResource {

    private final TaskMapper taskMapper;
    private final TaskService taskService;

    @Override
    public List<TaskLiteResponseDto> getAll() {
        log.debug("getAll - start");

        List<Task> tasks = taskService.getAll();
        List<TaskLiteResponseDto> result = taskMapper.toTasksLiteResponseDto(tasks);

        log.debug("getAll - end: result = {}", result);
        return result;
    }
}
```
