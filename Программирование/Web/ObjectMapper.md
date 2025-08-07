### 🧾 **ObjectMapper**

**Простыми словами:** `ObjectMapper` — это **основной класс в [[Jackson]]**, который умеет **преобразовывать Java-объекты в JSON и обратно**.

---

### ⚙️ **Когда использовать**

- Если нужно **вручную сериализовать** объект в JSON (Java → JSON)
    
- Или **вручную десериализовать** JSON в объект (JSON → Java)
    
- Когда не используешь [[Spring MVC]] или работаешь вне [[@RestController]]
    

---

### 📌 **Пример: Java → JSON**

```java
ObjectMapper mapper = new ObjectMapper();

User user = new User("Alice", 30);
String json = mapper.writeValueAsString(user);
System.out.println(json); // {"name":"Alice","age":30}
```

---

### 📌 **Пример: JSON → Java**

```java
String json = "{\"name\":\"Bob\",\"age\":25}";
User user = mapper.readValue(json, User.class);
```

---

### 🧠 **Особенности**

- Настраиваемый: можно включать/выключать сериализацию `null`, форматировать даты, управлять полями и т.д.
    
- Поддерживает:
    
    - списки и массивы
        
    - вложенные объекты
        
    - `Map<String, Object>`
        
- Работает с аннотациями Jackson:
    
    - `@JsonIgnore`
        
    - `@JsonProperty`
        
    - `@JsonFormat` и др.
        
- В [[Spring Boot]] используется автоматически под капотом в [[@RequestBody]] и [[@ResponseBody]]
    

---

### 🔗 **Связанные термины**

- [[Jackson]]
    
- [[JSON]]
    
- [[DTO]]
    
- [[@RequestBody]]
    
- [[@ResponseBody]]
    
- [[Spring MVC]]
    

---

#java #jackson #json #objectmapper #dto #spring