```java
// данный класс находится в проекте, по нему генерируется ProjectMapperImpl
// source: ilya-java-mentoring-task-tracker-spring-10/tasktrackerspring-impl/.../mapper/ProjectMapper.java
@Mapper
public interface ProjectMapper {

    ProjectResponseDto toProjectResponseDto(Project project);

    List<ProjectResponseDto> toProjectsResponseDto(List<Project> projects);

    Project toProject(ProjectCreateDto dto);
}
```

```java
// сгенерированный по ProjectMapper класс, который находится в target
@Generated(
    value = "org.mapstruct.ap.MappingProcessor",
    date = "2024-05-15T16:33:19+0300",
    comments = "version: 1.5.3.Final, compiler: Eclipse JDT (IDE) 3.38.0.v20240417-1011, environment: Java 17.0.10 (Eclipse Adoptium)"
)
@Component
public class ProjectMapperImpl implements ProjectMapper {

    @Override
    public ProjectResponseDto toProjectResponseDto(Project project) {
        if ( project == null ) {
            return null;
        }

        Long id = null;
        String name = null;
        String description = null;

        id = project.getId();
        name = project.getName();
        description = project.getDescription();

        ProjectResponseDto projectResponseDto = new ProjectResponseDto( id, name, description );

        return projectResponseDto;
    }

    @Override
    public List<ProjectResponseDto> toProjectsResponseDto(List<Project> projects) {
        if ( projects == null ) {
            return null;
        }

        List<ProjectResponseDto> list = new ArrayList<ProjectResponseDto>( projects.size() );
        for ( Project project : projects ) {
            list.add( toProjectResponseDto( project ) );
        }

        return list;
    }

    @Override
    public Project toProject(ProjectCreateDto dto) {
        if ( dto == null ) {
            return null;
        }

        Project project = new Project();

        project.setDescription( dto.description() );
        project.setName( dto.name() );

        return project;
    }
}
```
