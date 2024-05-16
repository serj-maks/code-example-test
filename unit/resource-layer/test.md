```java
@ActiveProfiles("test")
@ExtendWith(SpringExtension.class)
@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
public abstract class IntegrationTest {

    @Autowired
    protected TestRestTemplate restTemplate;

    @Autowired
    protected TransactionTemplate transactionTemplate;

    @Autowired
    protected UserRepository userRepository;

    @Autowired
    protected ProjectRepository projectRepository;

    @Autowired
    protected TaskRepository taskRepository;

    @AfterEach
    final void clean() {
        userRepository.deleteAll();
        projectRepository.deleteAll();
        taskRepository.deleteAll();
    }
}
```

```java
class TaskResourceImplTest extends IntegrationTest {

    @Test
    void getAll() {
        Project project1 = new Project()
            .setName("Sales")
            .setDescription("sales desc");
        User creator1 = new User()
            .setName("Ivan")
            .setEmail("ivan@gmail.com");
        Task task1 = new Task()
            .setTitle("task1 title")
            .setCreator(creator1)
            .setProject(project1);

        Project project2 = new Project()
            .setName("Develop")
            .setDescription("develop desc");
        User creator2 = new User()
            .setName("Motvey")
            .setEmail("motvey@gmail.com");
        Task task2 = new Task()
            .setTitle("task2 title")
            .setCreator(creator2)
            .setProject(project2);

        task1 = taskRepository.save(task1);
        task2 = taskRepository.save(task2);

        ResponseEntity<List<TaskLiteResponseDto>> response = restTemplate.exchange(
            "/api/tasks",
            HttpMethod.GET,
            null,
            new ParameterizedTypeReference<List<TaskLiteResponseDto>>() {
            }
        );

        assertEquals(response.getStatusCode(), HttpStatus.OK);

        TaskLiteResponseDto responseDtoTask1 = new TaskLiteResponseDto(task1.getId(), task1.getTitle());
        TaskLiteResponseDto responseDtoTask2 = new TaskLiteResponseDto(task2.getId(), task2.getTitle());
        List<TaskLiteResponseDto> actual = response.getBody();

        assertThat(actual).containsExactlyInAnyOrder(responseDtoTask1, responseDtoTask2);
    }
}
```
