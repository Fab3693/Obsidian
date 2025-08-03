### 🧾 **@ResponseBody**

**Простыми словами:** `@ResponseBody` говорит Spring, что **результат метода нужно вернуть напрямую в HTTP-ответ**, минуя шаблоны (HTML-страницы). Обычно это **JSON** или текст.

---

### ⚙️ **Когда использовать**

- Когда нужно вернуть [[JSON]], XML, строку, число и т.п.** в теле ответа
    
- При создании REST API
    
- Если не используешь [[@RestController]] (который включает `@ResponseBody` автоматически)
    

---

### 📌 **Пример: возвращаем JSON**

```java
[[ @Controller ]]
public class UserController {
    
    [[ @GetMapping("/user") ]]
    [[ @ResponseBody ]]
    public User getUser() {
        return new User("Alice", "alice@example.com");
    }
}
```

📍 Здесь `User` будет автоматически преобразован в JSON (через Jackson).

---

### 📌 **Если используется @RestController**

```java
[[ @RestController ]]
public class UserController {
    
    [[ @GetMapping("/user") ]]
    public User getUser() {
        return new User("Bob", "bob@example.com");
    }
}
```

📍 `@RestController` = `@Controller + @ResponseBody` для всех методов.

---

### 🧠 **Особенности**

- Используется для сериализации объекта в тело ответа (например, в JSON)
    
- Если вернуть строку — она будет содержимым ответа, а не именем шаблона
    
- Работает вместе с `HttpMessageConverter` (чаще всего Jackson)
    

---

### 🔗 **Связанные термины**

- [[@RestController]]
    
- [[@Controller]]
    
- [[@RequestMapping]]
    
- [[JSON]]
    
- [[Spring MVC]]
    

---

#spring #mvc #response #json #rest