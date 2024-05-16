```java
// source: ilya-java-mentoring-task-tracker-9/.../dao/impl/TaskDaoImpl.java
@Repository
@RequiredArgsConstructor
public class TaskDaoImpl implements TaskDao {

    private final JdbcTemplate jdbcTemplate;
    private final BeanPropertyRowMapper mapper = new BeanPropertyRowMapper(Task.class);

    @Override
    public void save(Task task) throws DataAccessException {
        jdbcTemplate.update("insert into task (title, description) values (?, ?)",
            task.getTitle(),
            task.getDescription());
    }

    // ...
}
```
