```java
@ExtendWith(SpringExtension.class)
@ContextConfiguration(classes = DatabaseConfig.class)
public abstract class AbstractIntegrationTest {

    @Autowired
    protected JdbcTemplate jdbcTemplate;
}
```

```java
@ExtendWith(MockitoExtension.class)
class TaskServiceImplTest {

    @Mock
    private TaskDao taskDaoMock;

    @InjectMocks
    private TaskServiceImpl taskService;

    @AfterEach
    void tearDown() {
        reset(taskDaoMock);
    }

    @Test
    void edit() {
        long id = 1L;
        Task oldTask = new Task(id, "title", null, Priority.NORMAL, Status.OPEN, "old description");
        Task task = new Task(id, "title", null, Priority.NORMAL, Status.OPEN, "new description");

        when(taskDaoMock.findById(id)).thenReturn(Optional.of(oldTask));
        taskService.edit(task);

        verify(taskDaoMock).update(task);
    }

    @Test
    void edit_shouldThrowNotFound() {
        long id = Long.MAX_VALUE;
        Task task = new Task(id, "title", null, Priority.NORMAL, Status.OPEN, "description");

        assertThrows(NotFoundException.class, () -> taskService.edit(task));
    }
}
```
