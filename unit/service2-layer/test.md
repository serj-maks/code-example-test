```java
@ExtendWith(MockitoExtension.class)
class TaskServiceTest {

    @Mock
    TaskRepository taskRepositoryMock;

    @InjectMocks
    TaskService taskService;

    @Mock
    UserService userService;

    @Spy
    TaskMapper taskMapper = Mappers.getMapper(TaskMapper.class);

    // данный вариант работает так-же, как и @Spy - мокает нужный маппер
//    TaskMapper taskMapper = Mappers.getMapper(TaskMapper.class);

//    @AfterEach
//    void tearDown() {
//        reset(taskRepositoryMock);
//    }

    @BeforeEach
    void before() {
        ReflectionTestUtils.setField(taskService, "taskMapper", taskMapper);
    }

    @Test
    void getAll() {
        Long id = 1L;
        List<Task> expected = List.of(new Task()
            .setId(id)
            .setTitle("task title"));

        when(taskRepositoryMock.findAll())
            .thenReturn(expected);
        List<Task> actual = taskService.getAll();

        assertEquals(expected, actual);
    }
}
```
