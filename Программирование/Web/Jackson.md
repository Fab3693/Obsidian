### 🧾 **Jackson**

**Простыми словами:** `Jackson` — это **библиотека для работы с JSON в Java**. Она позволяет **автоматически превращать Java-объекты в JSON и обратно**. Используется по умолчанию в [[Spring Boot]] и [[Spring MVC]].

---

### ⚙️ **Когда использовать**

- При создании [[REST API]], где нужно отправлять/принимать [[JSON]]
    
- При сериализации (Java → [[JSON]]) и десериализации ([[JSON]] → Java)
    
- Для работы с [[DTO]], когда данные приходят от клиента или отправляются клиенту
    

---

### 📌 **Пример: объект → JSON**

```java
public class User {
    private String name;
    private int age;
    // геттеры и сеттеры
}
```

```java
ObjectMapper mapper = new ObjectMapper();
String json = mapper.writeValueAsString(new User("Alice", 30));
```

📍 Результат:

```json
{"name":"Alice","age":30}
```

---

### 📌 **Пример: JSON → объект**

```java
String json = "{\"name\":\"Bob\",\"age\":25}";
User user = mapper.readValue(json, User.class);
```

---

### 🧠 **Особенности**

- Использует аннотации:
    
    - `@JsonProperty` — переименовать поле
        
    - `@JsonIgnore` — исключить поле
        
    - `@JsonInclude` — включать только непустые значения
        
    - `@JsonFormat` — задать формат (например, для даты)
        
- В [[Spring MVC]] сериализация происходит **автоматически** — просто верни объект из контроллера с [[@ResponseBody]] или [[@RestController]]
    
- Поддерживает вложенные объекты, списки, карты, даты и пр.
    

---

### 🔗 **Связанные термины**

- [[JSON]]
    
- [[DTO]]
    
- [[@ResponseBody]]
    
- [[@RequestBody]]
    
- [[Spring MVC]]
    
- [[ObjectMapper]]
    

---

#java #json #jackson #dto #spring #restapi