```java
import java.util.List;
import java.util.Optional;

public class DaoMock implements Dao<Poll> {

    @Override
    public List<Poll> findAll() throws DaoException {
        return List.of(
            new Poll(1L, "name", "description"),
            new Poll(2L, "name", "description"),
            new Poll(3L, "name", "description")
        );
    }

    @Override
    public Optional<Poll> findById(long id) throws DaoException {
        if (id == 1L) {
            return Optional.of(new Poll(id, "name", "description"));
        } else {
            return Optional.empty();
        }
    }
}
```

```java
import static org.junit.jupiter.api.Assertions.assertEquals;
import static org.junit.jupiter.api.Assertions.assertThrows;

import org.junit.jupiter.api.Test;

public class PollServiceImplTest {

    @Test
    void getById_ShouldReturnPoll() {
        PollServiceImpl pollServiceImpl = new PollServiceImpl(new DaoMock());
        long id = 1L;
        Poll expected = new Poll(1L, "name", "description");
        Poll actual = pollServiceImpl.getById(id);
        assertEquals(expected, actual);
    }

    @Test
    public void getByIdThrowsException() {
        PollServiceImpl pollServiceImpl = new PollServiceImpl(new DaoMock());
        long id = 2L;
        assertThrows(NotFoundException.class, () -> pollServiceImpl.getById(id));
    }
}
```
