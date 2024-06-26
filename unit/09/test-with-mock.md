```java
import static org.junit.jupiter.api.Assertions.assertEquals;
import static org.junit.jupiter.api.Assertions.assertThrows;
import static org.mockito.Mockito.reset;
import static org.mockito.Mockito.verify;
import static org.mockito.Mockito.when;

import java.util.Optional;

import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.extension.ExtendWith;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoExtension;

@ExtendWith(MockitoExtension.class)
public class PollServiceImplTest {

    @Mock
    private Dao<Poll> dao;

    @InjectMocks
    private PollServiceImpl pollService;

    @AfterEach
    void tearDown() {
        reset(dao);
    }

    @Test
    public void getById_ShouldReturnPoll() {
        long id = 1L;
        Poll expected = new Poll(id, "name", "description");
        when(dao.findById(id))
            .thenReturn(Optional.of(expected));

        Poll actual = pollService.getById(id);

        assertEquals(expected, actual);
        verify(dao).findById(id);
    }

    @Test
    public void getById_ThrowsException() {
        long id = 1L;
        assertThrows(NotFoundException.class, () -> pollService.getById(id));
    }
}

```
