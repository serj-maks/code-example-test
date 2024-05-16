```java
public class ProjectMapperImplTest {

    ProjectMapper projectMapper = Mappers.getMapper(ProjectMapper.class);

    @Test
    void toProjectResponseDto() {
        Project project = new Project()
            .setId(1L)
            .setName("Sales")
            .setDescription("sales desc");

        ProjectResponseDto dto = projectMapper.toProjectResponseDto(project);

        assertEquals(project.getId(), dto.id());
        assertEquals(project.getName(), dto.name());
        assertEquals(project.getDescription(), dto.description());
    }

    @Test
    void toProjectsResponseDto() {
        Project project = new Project()
            .setId(1L)
            .setName("Sales")
            .setDescription("sales desc");
        List<ProjectResponseDto> actualDtos = projectMapper.toProjectsResponseDto(List.of(project));

        ProjectResponseDto expectedDto = new ProjectResponseDto(1L, "Sales", "sales desc");
        List<ProjectResponseDto> expectedDtos = List.of(expectedDto);

        assertEquals(expectedDtos, actualDtos);
    }

    @Test
    void toProject() {
        ProjectCreateDto dto = new ProjectCreateDto("Sales", "sales desc");

        Project project = projectMapper.toProject(dto);

        assertEquals(project.getName(), dto.name());
        assertEquals(project.getDescription(), dto.description());
    }
}
```
