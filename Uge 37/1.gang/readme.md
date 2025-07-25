## Beskrivelse
Vi skal se på operativsystemets opgaver, herunder command shell og brug af git fra command prompten

## Forberedelse
### For windows brugere: ###
Opsætning af git bash terminal i IntelliJ: [Setting up git bash in IntelliJ](https://www.youtube.com/watch?v=3chFGUdKp9M)  

### Se disse videoer: ###
[Lecture 1: Course Overview + The Shell (2020)](https://www.youtube.com/watch?v=Z56Jmr9Z34Q)  
[Git Tutorial for Beginners: Command-Line Fundamentals](https://www.youtube.com/watch?v=HVsySz-h9r4)  

### Resourcer: ###
[Bash cheat sheet](https://github.com/RehanSaeed/Bash-Cheat-Sheet)  
[Git cheat sheet](https://education.github.com/git-cheat-sheet-education.pdf)

## Læringsmål
* Kune forklare operativsystemets overordnede funktion 
* Kunne anvende bash command shell 
* Kunne anvende git bash 

## Indhold
### Operativsystemer
<img src="assets/os.png" alt="Alt Text" width="300"> 
Definition: Et operativsystem (OS) er et program (software), der administrerer computerens hardware og software ressourcer.

* Primære Funktioner:
  - Ressourcestyring: CPU, hukommelse, I/O enheder.
  - Filsystem: Organisering af data i filer og mapper.
* Brugergrænseflade: CLI (Command Line Interface) og GUI (Graphical User Interface).
* Eksempler på OS:
  - Desktop OS: Windows, macOS, Linux
  - Server OS: Ubuntu Server, CentOS, Windows Server
  - Mobile OS: Android, iOS
  - Embedded OS: Real-time OS'er til specifik hardware

### Filsystem: Organisering af data i filer og mapper

Et filsystem er den måde, et operativsystem organiserer og gemmer data på en harddisk eller anden lagringsenhed. Det giver en hierarkisk struktur af mapper (kataloger), hvor hver mappe kan indeholde filer og undermapper.

Filsystemet gør det muligt for brugeren og systemet at finde og håndtere filer logisk og effektivt.

#### Eksempel på katalogstruktur:
```plaintext
/home/
├── student/
│   └── projekter/
│       ├── bash-opgave/
│       │   ├── script.sh
│       │   └── output.txt
│       ├── java-projekt/
│       │   ├── Main.java
│       │   └── README.md
│       └── noter.txt
```

Forklaring:
- Mapper vises med `/` efter navnet.
- Filer vises uden skråstreg.
- `projekter/` indeholder to undermapper med tilhørende filer.
- `noter.txt` er en fil direkte i `projekter/`.

Hver mappe og fil kan tilgås via sin fulde sti, fx:  
`/home/student/projekter/java-projekt/Main.java`

Denne struktur gør det let at holde filer adskilt og organiseret efter projekter eller formål.







