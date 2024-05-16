```java
@ExtendWith(SpringExtension.class)
@ContextConfiguration(classes = DatabaseConfig.class)
public abstract class AbstractIntegrationTest {

    @Autowired
    protected JdbcTemplate jdbcTemplate;
}
```

```java
class TaskDaoImplTest extends AbstractIntegrationTest {

    @Autowired
    TaskDao taskDao;

    @Test
    void save() {
        Task task = new Task();

        // id - auto_increment (see schema_create.sql)
        task.setTitle("title");
        // deadline - may be null (see schema_create.sql)
        // priority - "NORMAL" by default (see schema_create.sql)
        // status - "OPEN" by default (see schema_create.sql)
        task.setDescription("description");
        taskDao.save(task);

        assertEquals(1, JdbcTestUtils.countRowsInTable(jdbcTemplate, "task"));
    }
}
```
