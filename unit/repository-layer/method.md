```java
// source: ilya-java-mentoring-task-tracker-spring-10/tasktrackerspring-impl/.../repository/TaskRepository.java
@Repository
public interface TaskRepository extends JpaRepository<Task, Long> {

    boolean existsById(Long id);

    List<Task> findAllByAssigneeId(Long id);

    Page<Task> findAllByProjectId(Long id, Pageable pageable);
}
```
