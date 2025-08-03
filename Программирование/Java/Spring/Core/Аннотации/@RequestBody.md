### 🧾 **@RequestBody**

**Простыми словами:** `@RequestBody` говорит Spring, что **тело HTTP-запроса нужно преобразовать в объект Java**, обычно из JSON или XML, и передать его в параметр метода контроллера.

---

### ⚙️ **Когда использовать**

- При обработке POST, PUT и других запросов с данными в теле (JSON, XML, и т.п.)
    
- Для автоматического маппинга данных запроса в объект
    
- В REST API для приёма данных от клиента
    

---

### 📌 **Пример использования**

```java
[[ @RestController ]]
public class UserController {
    
    [[ @PostMapping("/users") ]]
    public User createUser([[ @RequestBody ]] User user) {
        return userService.save(user);
    }
}
```

📍 Spring автоматически преобразует JSON из тела запроса в объект `User`.

---

### 🧠 **Особенности**

- Работает с помощью `HttpMessageConverter` (чаще всего Jackson для JSON)
    
- Если формат тела запроса не совпадает с ожидаемым, будет ошибка
    
- Позволяет удобно работать с API, не парся вручную JSON или XML
    

---

### 🔗 **Связанные термины**

- [[@ResponseBody]]
    
- [[@PostMapping]]
    
- [[REST API]]
    
- [[Spring MVC]]
    

---

#spring #mvc #requestbody #json #rest