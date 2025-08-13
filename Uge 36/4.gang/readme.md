
# MockMVC, Mockito og test af Controller

## Beskrivelse
Vi skal se på forskellige slags test, og specifikt på unittest af controlleren.
## Forberedelse
Læs: [Software Quality: understanding the different types of software testing](https://www.tuleap.org/software-quality-different-types-software-testing)

Se videoer:

---
## Læringsmål
- At kunne forklare de forskellige testniveauer
- At kunne forklare mocking
- At kunne anvende MockMVC testværktøj
- At kunne anvende Mockito framework
- At kunne skrive unit tests af Controller klasser

---
## Indhold
- Testniveauer
- MockMVC
- @WebMVCTest
- Mockito
- Unittest af controllere
---
### Testniveauer
---
### MockMVC

- MockMVC er en klasse i Spring test framework, der bruges til at teste web-laget (controller-laget) i en Spring Boot-applikation.
- Med MockMVC kan man simulere HTTP-forespørgsler til Spring MVC-controllere og verificere, hvordan controlleren håndterer dem.
- MockMVC skaber simulerede HTTP-forespørgsler uden at starte en rigtig webserver.

Simulere HTTP GET forespørgsel
```java
 mockMvc.perform(get("/hello"));
```

Simulere HTTP GET forespørgsel og teste responsen
```java
 mockMvc.perform(get("/hello"))
                .andExpect(status().isOk())
                .andExpect(view().name("hello-world"));
```
---
### @WebMVCTest

- @WebMvcTest er en Spring Boot test-annotation, der bruges til at teste web-laget (controllerer)
- @WebMvcTest bruges ofte med MockMVC for at simulere HTTP-anmodninger uden at starte en rigtig server
- Loader kun web-laget (f.eks. controllere, konfiguration af Spring MVC), men ikke services eller repositories

---
### Mockito
___
## Aktiviteter









