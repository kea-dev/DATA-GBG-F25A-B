# Opgave 1: message endpoint

I denne opgave skal du implementere de grundlæggende lag i en REST-applikation i Spring Boot:

- En `Message` model
- Et `Repository`
- En `Service`
- En `Controller`

Opret et Spring Boot projekt: `message`
Opret pakkerne: `model`, `repository`, `service` og `controller` under projektets rodmappe
Start med at oprette de nødvendige Java-klasser som vist i nedenstående kodeeksempler. Følg rækkefølgen og læs forklaringerne til hvert lag.

## Model
```java
// Model-klassen der repræsenterer en besked.
// Den indeholder to felter: id og content, samt en konstruktør og getters.
public class Message {
    private int id;
    private String content;

    public Message(int id, String content) {
        this.id = id;
        this.content = content;
    }

    public int getId() {
        return id;
    }

    public String getContent() {
        return content;
    }
}
```

## Repository
```java
// Repository-klassen fungerer som et datalager i hukommelsen.
// Den opretter 3 beskeder ved opstart og returnerer dem via en metode
public class MessageRepository {
    private final List<Message> messages = new ArrayList<>();
    private int messageId = 1;

    public MessageRepository() {
        populateMessages();
    }

    private void populateMessages() {
        while (messageId <= 3) {
            messages.add(new Message(messageId, "Velkommen til " + messageId + ".semester"));
            messageId++;
        }
    }

    public List<Message> getAllMessages() {
        return messages;
    }
}

```
## Service
```java
// Service-laget indeholder forretningslogik og kalder repository-klassen.
// Repository injiceres via konstruktøren (dependency injection).
public class MessageService {
    private final MessageRepository repository;

    public MessageService(MessageRepository repository) {
        this.repository = repository;
    }

    public List<Message> getMessages() {
        return repository.getAllMessages();
    }
}
```

## Controller
```java
// Controller-klassen håndterer HTTP-anmodninger fra klienten.
// Den bruger @Controller i stedet for @RestController og returnerer data via ResponseEntity.
@Controller
public class MessageController {
    private final MessageService service;

    public MessageController() {
        this.service = new MessageService();
    }

    @GetMapping("/messages")
    public ResponseEntity<List<Message>> getMessages() {
        List<Message> messages = service.getMessages();
        return new ResponseEntity<>(messages, HttpStatus.OK);
    }
}
```


## Test det i browseren
Test applikationen i browseren

