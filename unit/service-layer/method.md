```java
// source: ilya-java-mentoring-task-tracker-9/.../service/impl/TaskServiceImpl.java
@Service
@RequiredArgsConstructor
public class TaskServiceImpl implements TaskService {

    private final TaskDao taskDao;

    // get task from command (presentation, UI) layer. This task will be call "oldTask",
    // that oldTask will be replace by update method
    @Override
    @Transactional
    public void edit(Task task) {
        Task oldTask = getById(task.getId());

        if(task.getDeadline() != null) {
            oldTask.setDeadline(task.getDeadline());
        }

        if(task.getStatus() != null) {
            oldTask.setStatus(task.getStatus());
        }

        if(task.getPriority() != null) {
            oldTask.setPriority(task.getPriority());
        }

        if(task.getDescription() != null) {
            oldTask.setDescription(task.getDescription());
        }

        taskDao.update(oldTask);
    }
}
```
