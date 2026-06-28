<div align="center">
<img src="assets/banner.svg" alt="Niranjan Sharma" width="100%"/>
</div>

<br/>

I build backend systems in Java. Currently in my first year of DAM at IES Abastos in Valencia, where I've been spending most of my time designing clean, layered architectures and figuring out how production software actually works.

Two projects I'm proud of:

- **[Mini AI Assistant](https://github.com/NiranjanSCodes/mini-ai-assistant)** — an intent-routing system with three specialised agents. The part I found most interesting was designing the `AIService` interface with a `default` method so subclasses don't have to re-implement shared behaviour.
- **[Banking System Java](https://github.com/NiranjanSCodes/banking-system-java)** — a Model → Service → View banking system with `TreeSet` for deduplication, full Java serialization for persistence, and a 2D array activity report. The architecture is the thing I'd show a senior engineer first.

I'm trilingual — English, Spanish, and Nepali — which shapes how I think about documentation and how I approach working with different teams.

Open to internships in Spain starting 2025–2026.

<br/>

<img src="assets/divider.svg" width="100%"/>

<br/>

## What I've built

<table>
<tr>
<td width="50%" valign="top">

**[mini-ai-assistant](https://github.com/NiranjanSCodes/mini-ai-assistant)**

A conversational assistant that routes messages to the right agent based on detected intent. Built with an interface → abstract class → three concrete implementations hierarchy. Each agent refuses questions outside its domain and redirects the user — which required designing intent detection that is strict enough to be useful but forgiving enough not to frustrate.

```
AIService (interface)
  └── Assistant (abstract)
        ├── MathAssistant
        ├── StudyAssistant
        └── ProgrammingAssistant
```

Conversations are persisted to a `.txt` log via `FileLogger`, which implements a separate `ConversationLogger` interface — keeping I/O concerns completely out of the response logic. Custom `AssistantException` with three constructors handles the error surface.

`Java` `OOP` `File I/O` `Collections` `Custom Exceptions`

</td>
<td width="50%" valign="top">

**[banking-system-java](https://github.com/NiranjanSCodes/banking-system-java)**

A banking management system with a clean three-layer separation. The model layer has two account hierarchies (`CuentaCorriente`, `CuentaAhorro`) and two card types (`TarjetaDebito`, `TarjetaCredito`), all implementing `Comparable` so they sort correctly in `TreeSet` collections without custom comparators.

```
Modelo  →  CuentaBancaria (abstract)
           Tarjeta (abstract)
           Cliente, Transaccion, TipoOperacion

Servicio →  Banco (TreeSet + serialization)

Vista   →  Menu (user interaction only)
```

The service layer serialises the full bank state to `datos.dat` on exit and restores it on startup. The `transient` keyword is used correctly on `DateTimeFormatter` — which is not serializable — so the compiler doesn't silently break persistence.

`Java` `Serialization` `TreeSet` `MVC` `Comparable`

</td>
</tr>
</table>

<br/>

<img src="assets/divider.svg" width="100%"/>

<br/>

## Stack

The technologies I've actually used in a shipped project.

| Technology | Used in |
|---|---|
| Java 24 | Both projects — primary language |
| Maven | `mini-ai-assistant` — build and dependency management |
| Git + GitHub | Both projects — version control |
| IntelliJ IDEA | Both projects — IDE |
| Java Collections API | Both projects — `TreeSet`, `HashSet`, `LinkedList`, `ArrayList`, `HashMap` |
| Java Serialization | `banking-system-java` — full object persistence |
| File I/O (`BufferedWriter`, `BufferedReader`) | `mini-ai-assistant` — conversation logging |
| Regex | `mini-ai-assistant` — input validation in `addKnowledge()` |

Learning next: Spring Boot, SQL, REST APIs.

<br/>

<img src="assets/divider.svg" width="100%"/>

<br/>

## A piece of code I'd show a senior engineer

In `banking-system-java`, the `Transaccion` class uses `transient` on `DateTimeFormatter`:

```java
private LocalDateTime fecha = LocalDateTime.now();
transient DateTimeFormatter format = DateTimeFormatter.ofPattern("dd/MM/yyyy");
```

`DateTimeFormatter` isn't serializable. Without `transient`, Java would throw a `NotSerializableException` at runtime when saving to `datos.dat` — silently breaking persistence for any transaction that carried a formatter reference. The fix is one keyword, but finding it requires understanding how Java serialization actually traverses the object graph.

It's a small thing. But it's the kind of thing that separates someone who read about serialization from someone who debugged it.

<br/>

<img src="assets/divider.svg" width="100%"/>

<br/>

## Currently

```
Building   →  banking-system-java: adding JUnit 5 tests to the service layer
Studying   →  DAM Year 1 · IES Abastos · Valencia, Spain
Reading    →  Effective Java, 3rd Edition — Joshua Bloch
```

<br/>

<img src="assets/divider.svg" width="100%"/>

<br/>

## Connect

**Niranjan Sharma** — Valencia, Spain

[LinkedIn](https://www.linkedin.com/in/niranjan-sharma-b9bb282ba) · [GitHub](https://github.com/NiranjanSCodes)

*English · Español · नेपाली*
