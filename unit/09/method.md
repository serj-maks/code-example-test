```java
// source: ilya-java-mentoring-poll-8/poll-service/.../impl/PollServiceImpl.java
public Poll getById(long id) {
    log.debug("getById - start");

    Poll poll = dao.findById(id)
        .orElseThrow(() -> new NotFoundException("poll with id = " + id + " not found"));

    log.debug("getById - end: poll = {}", poll);
    return poll;
}
```
