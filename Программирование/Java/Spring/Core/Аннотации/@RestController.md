### 🧾 **@RestController**

**Простыми словами:** `@RestController` — это аннотация в [[Spring MVC]], которая **обозначает класс как контроллер для REST API**, автоматически добавляя к каждому методу `@ResponseBody`. Это значит, что методы возвращают данные (обычно JSON), а не страницы.

---

### ⚙️ **Когда использовать**

- При создании RESTful сервисов и API
    
- Когда нужно возвращать данные (JSON, XML) в ответе без использования шаблонов
    
- Чтобы не писать `@ResponseBody` над каждым методом вручную
    

---

### 📌 **Пример использования**

```java
[[ @RestController ]]
public class UserController {
    
    [[ @GetMapping("/users") ]]
    public List<User> getAllUsers() {
        return userService.findAll();
    }
}
```

📍 Все методы класса возвращают данные напрямую, без HTML-страниц.

---

### 🧠 **Особенности**

- Комбинирует в себе `@Controller` + `@ResponseBody`
    
- Очень удобно для разработки REST API
    
- Работает с `HttpMessageConverter` для автоматического преобразования объектов в JSON, XML и т.д.
    

---

### 🔗 **Связанные термины**

- [[@Controller]]
    
- [[@ResponseBody]]
    
- [[@GetMapping]]
    
- [[REST API]]
    
- [[Spring MVC]]
    

---

#spring #mvc #restcontroller #restapi #json