```java
// source: ilya-java-mentoring-task-tracker-spring-10/tasktrackerspring-impl/.../service/TaskService.java
@Service
@RequiredArgsConstructor
public class TaskService {

    private final TaskRepository taskRepository;
    private final ProjectService projectService;
    private final UserService userService;
    private final TaskMapper taskMapper;

    @Transactional(readOnly = true)
    public List<Task> getAll() {
        return taskRepository.findAll();
    }
}
// line1
// line2
```
