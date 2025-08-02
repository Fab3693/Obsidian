### 📥 **GET**

**Простыми словами:** `GET` — это HTTP-запрос, с помощью которого **клиент получает данные от сервера**. Никаких изменений на сервере не происходит — только чтение.

---

#### 🧠 **Когда используется**

- Получение списка объектов: `GET /api/users`
    
- Получение конкретного объекта: `GET /api/users/42`
    

---

#### 📦 **В Spring MVC**

```java
@RestController
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}")
    public UserDTO getUser(@PathVariable Long id) {
        return userService.findById(id);
    }
}
```

- `@GetMapping` — специальная аннотация для `GET`-запросов.
    
- `@PathVariable` — извлекает `id` из URL.
    

---

#### 🧪 **Пример запроса с Postman или curl**

```bash
curl -X GET http://localhost:8080/api/users/42
```

Ответ:

```json
{
  "id": 42,
  "username": "julia"
}
```

---

#### 🧷 **Особенности**

- Безопасен (не изменяет данные)
    
- Идемпотентен (результат одинаков при повторном вызове)
    
- Можно кэшировать
    
- Подходит для ссылок и закладок
    

---

#### 🔗 **Связанные термины**

- [[REST API]]
    
- [[Spring MVC]]
    
- [[@GetMapping]]
    
- [[DTO]]
    
- [[JSON]]
    

---

#http #get #restapi #spring #controller