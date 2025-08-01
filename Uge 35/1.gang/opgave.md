# Opgave: message endpoint

I denne opgave skal du implementere de grundlæggende lag i en REST-applikation i Spring Boot:

- En `Message` model
- Et `Repository`
- En `Service`
- En `Controller`

Opret et Spring Boot projekt: `message`  
Opret pakkerne: `model`, `repository`, `service` og `controller` under projektets rodmappe.  
Start med at oprette de nødvendige Java-klasser som vist i nedenstående kodeeksempler.  
Følg rækkefølgen og læs forklaringerne til hvert lag.

## Model
```java
package org.example.message.model;

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
package org.example.message.repository;

import org.example.message.model.Message;
import org.springframework.stereotype.Repository;

import java.util.ArrayList;
import java.util.List;

@Repository
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
package org.example.message.service;

import org.example.message.model.Message;
import org.example.message.repository.MessageRepository;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
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
package org.example.message.controller;

import org.example.message.model.Message;
import org.example.message.service.MessageService;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;

import java.util.List;

@Controller
@RequestMapping("message")
// Controller-klassen håndterer HTTP-anmodninger fra klienten.
// Den bruger @Controller i stedet for @RestController og returnerer data via ResponseEntity.
public class MessageController {
    private final MessageService service;

    public MessageController(MessageService messageService) {
        this.service = messageService;
    }

    @GetMapping()
    public ResponseEntity<List<Message>> getMessages() {
        List<Message> messages = service.getMessages();
        return new ResponseEntity<>(messages, HttpStatus.OK);
    }
}
```


## Test det i browseren
Test applikationen i browseren.  
Gå til dette endpoint: `http://localhost:8080/message`  
Følgende output skulle gene vises:  
```text
[{"id": 1,"content": "Velkommen til 1.semester"},{"id": 2,"content": "Velkommen til 2.semester"},{"id": 3,"content": "Velkommen til 3.semester"}]
```
---
## Udvid apllikationen
Du skal nu tilføje en `@PathVariable` (id)  og en `@RequestParam` (caps) til controller get-endpointet.  
Controleren skal kunne modtage en en path til en bestem message, samt en request parameter, `caps`, der angiver om resultatet skal konverteres til store bogataver.  
Eksempelvis skal dette kald: `http://localhost:8080/message/2?caps=yes` give følgende output:  
```text
{"id": 2, "content": "VELKOMMEN TIL 2.SEMESTER"}
```
* Start med at lave repository metoden:
  ```java
   public Message findMessageById(int id) {
     // kode
    }
  ```
  Metoden skal returnere et Message objekt med et bestemt id hvis det findes, ellers null
* Skriv herefter service metoden:
  ```java
  public Message findMessageById(int id, String caps) {
    //kode
  }
  ```
  Metoden skal kalde repository metoden fidgMessageById(Id).  
  Hvis caps ikke er null og = "yes" skal message content laves om til store bogstaver.  
  Message objekt returneres til sidst.

* Skriv endelig controller metoden:
```java
    @GetMapping("{id}")
    public ResponseEntity<Message> getMessageById(@PathVariable int id, @RequestParam(required = false) String caps) {
      // kode
    }
```
Hvis message blev fundet skal metoden returnere message objekt samt statuskoden HttpStatus.OK  
Hvis message ikke blev fundet skal metoden returnere statuskoden HttpStatus.NOT_FOUND 
